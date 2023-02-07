<script setup>
import { names } from "@/data";

const options = reactive({
	gender: "",
	popularity: "",
	length: "",
});

const computeSelectedName = () => {
	const filterdName = names
		.filter((name) => name.gender === options.gender)
		.filter((name) => name.popularity === options.popularity)
		.filter((name) => {
			if (options.length === "All") return true;
			else return name.length === options.length;
		});

	namess.value = filterdName.map((name) => name.name);
};

const namess = ref([]);
</script>

<template>
	<div class="container">
		<h1>Baby Name Generator</h1>
		<p>Choose your options and click the "Find Names" buttom below</p>

		<div class="options-container">
			<div class="options-container">
				<h4>1) Choose a gender</h4>
				<div class="option-button">
					<button
						:class="options.gender === 'Boy' && 'active'"
						@click="options.gender = 'Boy'"
					>
						Boy
					</button>
					<button
						:class="options.gender === 'Unisex' && 'active'"
						@click="options.gender = 'Unisex'"
					>
						Unisex
					</button>
					<button
						:class="options.gender === 'Girl' && 'active'"
						@click="options.gender = 'Girl'"
					>
						Girl
					</button>
				</div>
			</div>
			<div class="options-container">
				<h4>2) Choose the name popularity</h4>
				<div class="option-button">
					<button
						:class="options.popularity === 'Trendy' && 'active'"
						@click="options.popularity = 'Trendy'"
					>
						Trendy
					</button>
					<button
						:class="options.popularity === 'Uniqu' && 'active'"
						@click="options.popularity = 'Uniqu'"
					>
						Uniqu
					</button>
				</div>
			</div>
			<div class="options-container">
				<h4>3) Choose the name length</h4>
				<div class="option-button">
					<button
						:class="options.length === 'Long' && 'active'"
						@click="options.length = 'Long'"
					>
						Long
					</button>
					<button
						:class="options.length === 'All' && 'active'"
						@click="options.length = 'All'"
					>
						All
					</button>
					<button
						:class="options.length === 'Short' && 'active'"
						@click="options.length = 'Short'"
					>
						Short
					</button>
				</div>
			</div>
			<button @click="computeSelectedName">Find Name</button>
		</div>

		{{ namess }}
	</div>
</template>

<style scoped>
.container {
	background-color: gray;
	width: 500px;
	margin: 0 auto;
	text-align: center;
}
.active {
	border: 2px solid red;
}
</style>
