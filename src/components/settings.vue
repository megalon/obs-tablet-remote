<template>
	<overlay modal-class="wide" @overlay-click="showSettings(false)">
		<div class="modal-header">
			<h2 class="title">Global Settings</h2>
			<button class="close" @click="showSettings(false)"></button>
		</div>

		<div class="settings-container">
			<div class="settings-group">
				<h3>Danger Zone</h3>
				<button @click="askForReset">Reset Layout</button>
			</div>
		</div>
	</overlay>
</template>

<script>
	import {mapMutations} from 'vuex'

	import Overlay from './overlay'

	export default {
		components: {
			Overlay
		},
		methods: {
			askForReset() {
				// eslint-disable-next-line no-alert
				if (confirm('Are you sure you want to reset the layout?')) {
					this.resetLayout()
				}
			},
			...mapMutations(['showSettings']),
			...mapMutations('layout', ['resetLayout'])
		}
	}
</script>
