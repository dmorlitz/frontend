<template>
	<div class="no-auth-wrapper">
		<div class="noauth-container">
			<Logo class="logo" width="400" height="117" />
			<Message v-if="motd !== ''" class="my-2">
				{{ motd }}
			</Message>
			<slot/>
		</div>
	</div>
</template>

<script lang="ts" setup>
import Logo from '@/components/home/Logo.vue'
import Message from '@/components/misc/message.vue'
import {useStore} from 'vuex'
import {computed} from 'vue'

const store = useStore()
const motd = computed(() => store.state.config.motd)
</script>

<style lang="scss" scoped>
.no-auth-wrapper {
	background: url('@/assets/llama.svg?url') no-repeat bottom left fixed var(--site-background);
	min-height: 100vh;
}

.noauth-container {
	max-width: 450px;
	width: 100%;
	margin: 0 auto;
	padding: 1rem;
}

.logo {
	color: var(--logo-text-color);
	max-width: 100%;
}
</style>
