<template>
	<div class="change">
		<main>
			<section>
				<h2>Ajouter un étudiant</h2>
				<form @submit="submitCreateStudent">
					<label for="student">
						<span>Nom de l'étudiant</span>
						<input type="text" name="student" v-model="student" required />
					</label>
					<label for="classe">
						<span>Classe</span>
						<input type="text" name="classe" v-model="classe" required />
					</label>
					<button type="submit">Click Here</button>
				</form>
			</section>
			<hr />
			<section>
				<h2>Modifier un étudiant</h2>
				<form @submit="submitUpdateStudent">
					<label for="student">
						<span>Nom de l'étudiant</span>
						<select name="student" id="">
							<option
								v-for="studentName in studentsName"
								:value="studentName"
								:key="studentName"
							>
								{{ studentName }}
							</option>
						</select>
					</label>
					<label for="day">
						<span>Jour</span>
						<input type="text" name="day" v-model="day" required />
					</label>
					<label for="link">
						<span>Lien</span>
						<input type="text" name="link" v-model="link" required />
					</label>
					<label for="title">
						<span>Titre</span>
						<input type="text" name="title" v-model="title" required />
					</label>
					<button type="submit">Click Here</button>
				</form>
			</section>
		</main>
	</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios, { AxiosResponse } from "axios";

interface Student {
	_id: string;
	name: string;
	class: string;
	cours: {
		_id: string;
		__v: number;
		month: string;
		lessons: {
			_id: string;
			day: string;
			title: string;
			link: string;
		}[];
	}[];
}

interface DataComponent {
	studentsName: string[];
	student: string;
	classe: string;
	day: string;
	link: string;
	title: string;
}

export default defineComponent({
	name: "Change",
	data(): DataComponent {
		return {
			studentsName: [],
			student: "",
			classe: "",
			day: "",
			link: "",
			title: "",
		};
	},
	methods: {
		async submitCreateStudent() {
			const response: AxiosResponse = await axios.post(
				"http://localhost:3000/api/students",
				{
					name: this.student,
					class: this.classe,
				}
			);
			console.log(response);
		},
		async submitUpdateStudent() {
			const response: AxiosResponse = await axios.put(
				`http://localhost:3000/api/students/${this.student}`,
				{
					day: this.day,
					link: this.link,
					title: this.title,
				}
			);
			console.log(response);
		},
	},
	mounted() {
		axios
			.get("https://sheltered-basin-99154.herokuapp.com/api/student/")
			.then(
				(response: AxiosResponse<{ message: string; students: Student[] }>) => {
					response.data.students.forEach((student: Student) => {
						this.studentsName?.push(student.name);
					});
				}
			);
	},
});
</script>

<style scoped lang="scss">
.change {
	main {
		section {
			width: 60vw;
			margin: auto 20vh;
			h2 {
				font-size: 2em;
				margin-bottom: 1vh;
			}
			form {
				display: flex;
				flex-direction: column;
				label {
					margin-bottom: 2vh;
					span {
						margin-right: 0.5vw;
					}
				}
			}
		}
	}
	hr {
		display: block;
		border: 1px solid white;
		width: 40vw;
		margin-top: 5vh;
		margin-bottom: 5vh;
		text-align: center;
	}
}
</style>
