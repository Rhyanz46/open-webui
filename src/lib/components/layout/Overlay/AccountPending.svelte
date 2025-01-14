<script lang="ts">
	import { getAdminDetails } from '$lib/apis/auths';
	import { onMount, tick, getContext } from 'svelte';

	const i18n = getContext('i18n');

	let adminDetails = null;

	onMount(async () => {
		adminDetails = await getAdminDetails(localStorage.token).catch((err) => {
			console.error(err);
			return null;
		});
	});
</script>

<div class="fixed w-full h-full flex z-[999]">
	<div
		class="absolute w-full h-full backdrop-blur-lg bg-white/10 dark:bg-gray-900/50 flex justify-center"
	>
		<div class="m-auto pb-10 flex flex-col justify-center">
			<div class="max-w-md">
				<!-- <div class="text-center dark:text-white text-2xl font-medium z-50">
					{$i18n.t('Account Activation Pending')}<br />
					{$i18n.t('Contact Admin for WebUI Access')}
				</div> -->

				<!-- <div class=" mt-4 text-center text-sm dark:text-gray-200 w-full">
					{$i18n.t('Your account status is currently pending activation.')}<br />
					{$i18n.t(
						'To access the WebUI, please reach out to the administrator. Admins can manage user statuses from the Admin Panel.'
					)}
				</div> -->

				<!-- {#if adminDetails}
					<div class="mt-4 text-sm font-medium text-center">
						<div>{$i18n.t('Admin')}: {adminDetails.name} ({adminDetails.email})</div>
					</div>
				{/if} -->


				<!-- makeai start-->
				<div class="mt-4 w-full p-4 text-center bg-white border border-gray-200 rounded-lg shadow sm:p-8 dark:bg-gray-800 dark:border-gray-700">
					<h5 class="mb-2 text-3xl font-bold text-gray-900 dark:text-white">Select Package</h5>
					<ul class="mt-4 grid w-full gap-2 md:grid-cols-1">
						<li>
							<input type="radio" id="hosting-small" name="hosting" value="hosting-small" class="hidden peer">
							<label for="hosting-small" class="inline-flex items-center justify-between w-full p-5 rounded-lg cursor-pointer peer-checked:text-green-600 bg-gray-700 peer-checked:bg-gray-100 hover:text-white hover:bg-gray-400">
								<div class="block">
									<div class="w-full text-lg font-semibold">Rp 1000</div>
									<div class="w-full">/day</div>
								</div>
								<svg class="w-5 h-5 ms-3 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
									<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
								</svg>
							</label>
						</li>
						<li>
							<input type="radio" id="hosting-so-big" name="hosting" value="hosting-so-big" class="hidden peer">
							<label for="hosting-so-big" class="inline-flex items-center justify-between w-full p-5 rounded-lg cursor-pointer peer-checked:text-green-600 bg-gray-700 peer-checked:bg-gray-100 hover:text-white hover:bg-gray-400">
								<div class="block">
									<div class="w-full text-lg font-semibold">Rp 30.0000</div>
									<div class="w-full">/month</div>
								</div>
								<svg class="w-5 h-5 ms-3 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
									<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
								</svg>
							</label>
						</li>
						<li>
							<input type="radio" id="hosting-big" name="hosting" value="hosting-big" class="hidden peer">
							<label for="hosting-big" class="inline-flex items-center justify-between w-full p-5 rounded-lg cursor-pointer peer-checked:text-green-600 bg-gray-700 peer-checked:bg-gray-100 hover:text-white hover:bg-gray-400">
								<div class="block">
									<div class="w-full text-lg font-semibold">Rp 15.0000</div>
									<div class="w-full">/month</div>
								</div>
								<svg class="w-5 h-5 ms-3 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
									<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
								</svg>
							</label>
						</li>
					</ul>
				</div>
				<!-- makeai end-->
			

				<div class=" mt-6 mx-auto relative group w-fit">
					<button
						class="relative z-20 flex px-5 py-2 rounded-full bg-white border border-gray-100 dark:border-none hover:bg-gray-100 text-gray-700 transition font-medium text-sm"
						on:click={async () => {
							location.href = '/';
						}}
					>
						{$i18n.t('Check Again')}
					</button>

					<button
						class="text-xs text-center w-full mt-2 text-gray-400 underline"
						on:click={async () => {
							localStorage.removeItem('token');
							location.href = '/auth';
						}}>{$i18n.t('Sign Out')}</button
					>
				</div>
			</div>
		</div>
	</div>
</div>
