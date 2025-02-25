<template>
	<section class="content page-about flex flex-col h-full sm:flex-row">
		<PageSide side="left" :links="links" />
		<PageSide side="right">
			<ThemeToggle />
		</PageSide>

		<div class="general-data flex flex-col">
			<h3
				class="page-title font-light text-2xl page-name mb-12 block sm:hidden"
			>
				About me
			</h3>
			<div
				class="photo flex items-center justify-center h-full overflow-hidden"
			>
				<!--        <img src="img/photo-resume.png" alt="photo-resume">-->
				<img src="@/images/photo-resume.png" alt="photo-resume" />
			</div>
			<div class="personal-data p-6 flex flex-col space-y-4 h-max">
				<div
					class="personal-data__main flex justify-between items-start"
				>
					<div class="personal-data__name flex flex-col">
						<h4 class="font-semibold text-lg leading-normal">
							Yevhenii Yermolenko
						</h4>
						<p class="text-color-gray font-regular">Ukraine</p>
					</div>
					<p class="text-color-gray text-lg font-regular years">
						{{ getAgeFromBirthday(7, 4, 2000) }} years
					</p>
				</div>
				<div class="personal-data__experience font-regular">
					<p class="text-color-gray experience">
						Experience
						<span class="primary-font"
							>{{ getAgeFromBirthday(1, 1, 2023) }} year{{
								getAgeFromBirthday(1, 1, 2023) > 1 ? "s" : ""
							}}</span
						>
					</p>
				</div>
				<div
					class="personal-data__langs flex justify-between items-center space-x-4"
				>
					<div class="lang flex space-x-1">
						<span class="text-color-gray">EN</span>
						<span class="text-color-gray">-</span>
						<span class="primary-font">A2</span>
					</div>
					<div class="divide"></div>
					<div class="lang flex space-x-1">
						<span class="text-color-gray">PL</span>
						<span class="text-color-gray">-</span>
						<span class="primary-font">B1</span>
					</div>
					<div class="divide"></div>
					<div class="lang flex space-x-1">
						<span class="text-color-gray">UA</span>
						<span class="text-color-gray">-</span>
						<span class="primary-font">C2</span>
					</div>
					<div class="divide"></div>
					<div class="lang flex space-x-1">
						<span class="text-color-gray">RU</span>
						<span class="text-color-gray">-</span>
						<span class="primary-font">C2</span>
					</div>
				</div>
				<div class="download-resume">
					<button
						v-if="!openedTypesFile"
						class="w-full button primary primary-border py-3 flex space-x-2 justify-center primary-font"
						@click="switchTypesFile"
					>
						<svg
							width="22"
							height="22"
							viewBox="0 0 22 22"
							fill="none"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								d="M7 11L11 15.232L15 11.041M11 4V15M5 18H17"
								stroke="#FFCD1C"
								stroke-linecap="round"
								stroke-linejoin="round"
							/>
						</svg>
						Download resume
					</button>
					<div
						v-else
						class="download-buttons flex items-center pl-4 space-x-4"
						@click="switchTypesFile"
					>
						<p>Language</p>
						<div class="flex grow">
							<a
								v-for="CV in CVs"
								:key="CV.label"
								:href="CV.href"
								target="_blank"
								class="lang__button py-3 grow text-center"
								>{{ CV.label }}</a
							>
						</div>
					</div>
				</div>
			</div>
		</div>
		<div class="main-data p-16 pb-6 w-full overflow-y-auto">
			<h3
				class="page-title font-light text-2xl page-name mb-12 hidden sm:block"
			>
				About me
			</h3>
			<header class="font-bold text-2xl mb-16">
				<h2 class="mb-6 text-4xl leading-normal">
					Hi, my name's Eugene!
				</h2>
				<h4 class="leading-normal">
					I am a UI/UX designer and front-end developer in one person.
					I have been engaged in design for about 3 years, I have met
					many projects and interesting tasks on my professional path.
				</h4>
			</header>
			<section
				class="my-mind w-full flex sm:flex-row space-x-0 sm:space-x-16 space-y-8 sm:space-y-0"
			>
				<div class="w-full sm:w-1/2">
					<h5 class="primary-font main-idea font-bold mb-4 relative">
						My main idea
					</h5>
					<p class="font-regular text-color-gray mb-3">
						I believe that the key factor influencing the
						profitability and success of any product is its design,
						BUT.
					</p>
					<p class="font-regular text-color-gray mb-3">
						The design is not in the form of a visual design, but in
						terms of how the end user will interact throughout the
						entire cycle of working with the product.
					</p>
					<p class="font-regular text-color-gray">
						Design is not how an object looks, but how it works.
						Design is design, from idea to practical implementation.
					</p>
				</div>
				<div class="w-full sm:w-1/2">
					<h5 class="primary-font font-bold mb-4">
						Free time forwarding
					</h5>
					<p class="font-regular text-color-gray mb-3">
						In my free time, I develop my professional skills and
						learn new ones in related fields in order to better
						understand what programmers face when implementing
						design solutions.
					</p>
					<p class="font-regular text-color-gray mb-3">
						Sometimes I need a “reboot". A walk around the city with
						a cup of coffee helps me with this)
					</p>
					<p class="font-regular text-color-gray mb-3">
						I also run my Instagram blog, where I talk about the
						field of design and give useful tips to the audience
					</p>
					<a
						target="_blank"
						href="https://www.instagram.com/_uixer_/"
						class="mt-4 leading-none link blue flex items-center font-regular"
					>
						Instagram
						<i class="bx bx-right-arrow-alt text-xl ml-1"></i>
					</a>
				</div>
			</section>
			<section class="certificates mt-6">
				<h5 class="primary-font font-bold mb-4">Certificates</h5>
				<div
					class="certificates-list grid grid-cols-1 sm:grid-cols-2 gap-5 flex-wrap"
				>
					<div
						v-for="certificate in certificates"
						:key="certificate.id"
						class="certificate flex flex-col h-min"
					>
						<div
							class="certificate__header header flex flex-col space-y-2 justify-center items-center py-10 px-3"
						>
							<h3
								class="header__main font-bold text-3xl leading-none"
								:style="{ color: certificate.color }"
							>
								{{ certificate.label }}
							</h3>
							<span class="font-light text-sm">
								{{ certificate.type }}
							</span>
						</div>
						<Accordion class="certificate__accordion">
							<AccordionTab
								header="Certificates"
								contentClass="certificate__accordion accordion"
							>
								<a
									v-for="certificateItem in certificate.list_cert"
									:key="certificateItem.id"
									:href="certificateItem.href"
									class="accordion__item flex justify-between font-thin hover:underline underline-offset-4 transition-none py-3 first:pt-0 last:pb-0"
								>
									<span>{{ certificateItem.name }}</span>
									<span>open</span>
								</a>
							</AccordionTab>
						</Accordion>
					</div>
				</div>
			</section>
		</div>
	</section>
</template>

<script setup>
import PageSide from "@/components/elements/PageSide.vue";
import ThemeToggle from "@/components/ThemeToggle.vue";
import { ref } from "vue";

const links = [
	{
		name: "skills",
		href: "skills",
	},
	{
		name: "about me",
		href: "about",
	},
	{
		name: "projects",
		href: "projects",
	},
];
const certificates = [
	{
		id: 1,
		label: "Angular",
		type: "JS framework",
		color: "#ff0032",
		list_cert: [
			{
				id: 11,
				name: "certificate 1",
				href: "",
			},
			{
				id: 12,
				name: "certificate 2",
				href: "",
			},
			{
				id: 13,
				name: "certificate 3",
				href: "",
			},
		],
	},
	{
		id: 2,
		label: "VUE",
		type: "JS framework",
		color: "#0db96d",
		list_cert: [
			{
				id: 21,
				name: "certificate 1",
				href: "",
			},
			{
				id: 22,
				name: "certificate 2",
				href: "",
			},
			{
				id: 23,
				name: "certificate 3",
				href: "",
			},
		],
	},
	{
		id: 2,
		label: "React",
		type: "JS framework",
		color: "#04c2c2",
		list_cert: [
			{
				id: 31,
				name: "certificate 1",
				href: "",
			},
			{
				id: 32,
				name: "certificate 2",
				href: "",
			},
			{
				id: 33,
				name: "certificate 3",
				href: "",
			},
		],
	},
];
const CVs = [
	{
		href: "./src/documents/CV-Yevhenii Yermolenko.pdf",
		label: "EN",
	},
	{
		href: "./src/documents/CV-Yevhenii Yermolenko.pdf",
		label: "PL",
	},
	{
		href: "./src/documents/CV-Yevhenii Yermolenko.pdf",
		label: "UA",
	},
];
const openedTypesFile = ref(false);

const getAgeFromBirthday = (day, month, year) => {
	let b_date = new Date(year, month, day);
	let today = new Date();
	today.setHours(0);
	today.setMinutes(0);
	today.setSeconds(0);
	return Math.floor((today - b_date) / 31556952000);
};
const switchTypesFile = () => {
	console.log(openedTypesFile.value);

	openedTypesFile.value = !openedTypesFile.value;
};
</script>

<style lang="scss" scoped>
@import "@/assets/variables";

.general-data {
	width: 30%;
}

.photo {
	position: relative;

	img {
		position: absolute;
		height: 100%;
		width: 100%;
		object-fit: cover;
	}
}

.main-data {
	padding-left: 5%;
	padding-right: 5%;
	margin-right: 16px;
}

.personal-data__langs {
	.divide {
		height: 18px;
		width: 1px;
	}
}

.pages-links {
	z-index: 1000;
	border-bottom: 1px solid $lines;

	& .main-link {
		& .dot {
			background: $text-color;
		}

		&:after {
			background: $lines;
		}
	}
}
</style>
