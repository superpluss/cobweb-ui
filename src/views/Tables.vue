<!-- 
	This is the tables page, it uses the dashboard layout in: 
	"./layouts/Dashboard.vue" .
 -->

<template>
	<div>
		<!-- Projects Table -->
		<a-row :gutter="24" type="flex">
			<!-- Projects Table Column -->
			<a-col :span="24" class="mb-24">
				<!-- Projects Table Column -->
				<CardProjectTable2 :data="table2Data" :columns="table2Columns"></CardProjectTable2>
				<!-- / Projects Table Column -->
			</a-col>
			<!-- / Projects Table Column -->
		</a-row>
		<!-- / Projects Table -->
	</div>
</template>

<script setup lang="ts">

// "Projects" table component.
import CardProjectTable2 from '@/components/Cards/CardProjectTable2.vue'

// "Projects" table list of columns and their properties.
const table2Columns = [
	{
		title: 'COMPANIES',
		dataIndex: 'company',
		slots: { customRender: 'company' },
		width: 300,
	},
	{
		title: 'BUDGET',
		dataIndex: 'budget',
		class: 'font-semibold text-muted',
	},
	{
		title: 'STATUS',
		dataIndex: 'status',
		class: 'font-semibold text-muted text-sm',
	},
	{
		title: 'EXEC',
		slots: { customRender: 'editExec' },
		width: 100,
	},
];

// "Projects" table list of rows and their properties.
const table2Data = [
	{
		key: '1',
		company: {
			name: 'Spotify Version',
			logo: '/images/logos/logo-spotify.svg',
		},
		status: "working",
		budget: '$14,000',
		completion: 60,
	},
	{
		key: '2',
		company: {
			name: 'Progress Track',
			logo: '/images/logos/logo-atlassian.svg',
		},
		status: "working",
		budget: '$3,000',
		completion: 10,
	},
	{
		key: '3',
		company: {
			name: 'Jira Platform Errors',
			logo: '/images/logos/logo-slack.svg',
		},
		status: "done",
		budget: 'Not Set',
		completion: {
			status: 'success',
			value: 100,
		},
	},
	{
		key: '4',
		company: {
			name: 'Launch new Mobile App',
			logo: '/images/logos/logo-spotify.svg',
		},
		status: "canceled",
		budget: '$20,600',
		completion: {
			status: 'exception',
			value: 50,
		},
	},
	{
		key: '5',
		company: {
			name: 'Web Dev',
			logo: '/images/logos/logo-webdev.svg',
		},
		status: "working",
		budget: '$4,000',
		completion: 80,
	},
	{
		key: '6',
		company: {
			name: 'Redesign Online Store',
			logo: '/images/logos/logo-invision.svg',
		},
		status: "canceled",
		budget: '$2,000',
		completion: {
			status: 'exception',
			value: 0,
		},
	},
];
</script>

<style lang="scss">
</style>