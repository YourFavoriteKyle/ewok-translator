<script lang="ts">
	import { page } from '$app/stores';
	import PrimaryButton from '$lib/components/buttons/primary.svelte';
</script>

<li class="profile">
	<input type="checkbox" id="profile-toggle" />
	<label for="profile-toggle" class="toggle">
		<div class="img-container">
			<img src={$page.data.session?.user.user_metadata.avatar_url} alt="User Avatar" />
		</div>
	</label>
	<div class="dropdown">
		<img src={$page.data.session?.user.user_metadata.avatar_url} alt="User Avatar" />
		<p class="username">{$page.data.session?.user.user_metadata.name}</p>
		<p class="email">{$page.data.session?.user.user_metadata.email}</p>
		<PrimaryButton method={'POST'} action={'?/signout'}>Sign Out</PrimaryButton>
	</div>
</li>

<style>
	/* PROFILE STYLE */
	.img-container {
		height: 2.5rem;
		width: 2.5rem;
	}
	img {
		border-radius: 50%;
	}
	.dropdown img {
		margin: 0 auto;
	}
	.profile {
		display: inline-block;
		position: relative;
	}
	.dropdown {
		background-color: white;
		padding: 1rem;
		position: absolute;
		right: 0;
		display: none;
		border-radius: 0.5rem;
		top: 4.5rem;
		text-align: center;
		filter: drop-shadow(0rem 0rem 0.5rem var(--nord3));
	}
	.username {
		font-size: 1.25rem;
	}
	.email {
		font-size: 1rem;
	}
	/* RESPONSIVE */
	#profile-toggle {
		display: none;
	}
	.toggle {
		user-select: none;
	}
	#profile-toggle:checked ~ .dropdown {
		display: block;
	}
	/* MEDIA QUERY */
	@media (max-width: 768px) {
		.profile {
			margin: 0.75rem 0 0 0;
		}
		.dropdown {
			right: -250%;
		}
	}
</style>
