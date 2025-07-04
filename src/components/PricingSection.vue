<template>
	<section id="pricing" class="relative min-h-screen w-full overflow-x-hidden" style="touch-action: manipulation;">
		<div class="relative z-10 max-w-7xl mx-auto py-24 px-6">
			<!-- text  -->
			<div>
				<div class="text-center mb-16">
					<h2 class="text-4xl md:text-[42px] font-bold tracking-[-0.4px] text-white mb-6">
						Plans & Pricing
					</h2>
					<p class="text-[22px] font-medium max-w-xl mx-auto">
						Startup Framework is free forever — you only pay for custom domain
						hosting or to export your site.
					</p>
				</div>
			</div>

			<!-- tables -->
			<div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
				<div v-for="(plan, index) in plans" :key="index"
					class="relative rounded-2xl border-2 border-white/20 p-8 py-14 transition-all duration-300 hover:bg-white/10">
					<!-- plan header -->
					<div class="mb-8 ml-7">
						<h3 class="text-[22px] font-medium text-white mb-6">
							{{ plan.name }}
						</h3>
						<div class="flex mb-6">
							<span class="text-[58px] font-bold text-white">{{
								plan.price
							}}</span>
							<span class="text-base text-white/80 mt-4 ml-1">{{
								plan.period
							}}</span>
						</div>
					</div>

					<!-- lists-->
					<ul class="space-y-4 mb-8">
						<li v-for="(feature, featureIndex) in plan.features" :key="featureIndex"
							class="flex items-center">
							<Check :class="[
								'w-4 h-4 mr-3 flex-shrink-0',
								feature.included ? 'text-green-400' : 'text-white/0',
							]" />
							<span :class="[
								'text-base',
								feature.included ? 'text-white' : 'text-white/70',
							]">
								{{ feature.name }}
							</span>
						</li>
					</ul>

					<!-- button -->
					<div class="w-full flex justify-center">
						<button :class="[
							'mx-auto w-[230px] h-[60px] py-3 px-6 rounded-full text-[20px] font-medium transition-all duration-200 transform hover:scale-105',
							plan.popular
								? 'bg-[#E93A7D] hover:bg-red-600 text-white'
								: 'bg-transparent border-2 border-white/30 text-white hover:bg-red-600 hover:border-red-600',
						]">
							{{ plan.buttonText }}
						</button>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<script setup>
import { Check } from "lucide-vue-next";

const plans = [
	{
		name: "Starter",
		price: "9.99",
		period: "$",
		features: [
			{ name: "2 GB of space", included: true },
			{ name: "14 days of backups", included: true },
			{ name: "Social integrations", included: true },
			{ name: "Client billing", included: true },
			{ name: "Remote access", included: false },
			{ name: "Custom domain", included: false },
			{ name: "24 hours support", included: false },
			{ name: "Admin tools", included: false },
			{ name: "Collaboration tools", included: false },
			{ name: "User management", included: false },
		],
		popular: false,
		buttonText: "Get Started",
	},
	{
		name: "Professional",
		price: "19.99",
		period: "$",
		features: [
			{ name: "2 GB of space", included: true },
			{ name: "14 days of backups", included: true },
			{ name: "Social integrations", included: true },
			{ name: "Client billing", included: true },
			{ name: "Remote access", included: true },
			{ name: "Custom domain", included: true },
			{ name: "24 hours support", included: true },
			{ name: "Admin tools", included: false },
			{ name: "Collaboration tools", included: false },
			{ name: "User management", included: false },
		],
		popular: true,
		buttonText: "Get Started",
	},
	{
		name: "Team",
		price: "49.99",
		period: "$",
		features: [
			{ name: "2 GB of space", included: true },
			{ name: "14 days of backups", included: true },
			{ name: "Social integrations", included: true },
			{ name: "Client billing", included: true },
			{ name: "Remote access", included: true },
			{ name: "Custom domain", included: true },
			{ name: "24 hours support", included: true },
			{ name: "Admin tools", included: true },
			{ name: "Collaboration tools", included: true },
			{ name: "User management", included: true },
		],
		popular: false,
		buttonText: "Get Started",
	},
];
</script>
