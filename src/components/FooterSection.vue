<template>
	<footer id="footer">
		<div class="relative max-w-7xl mx-auto py-20 px-6 md:px-16">
			<!-- top part -->
			<div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center mb-8">
				<div class="flex justify-center md:justify-start items-center">
					<h3 class="text-2xl font-bold text-white">Startup 3</h3>
				</div>
				<div class="flex justify-center md:justify-end items-center gap-4 text-white">
					<a href="#">Privacy Policy</a>
					<a href="#">Terms</a>
					<a href="https://facebook.com" target="_blank" rel="noopener">
						<font-awesome-icon :icon="['fab', 'facebook-f']" />
					</a>
					<a href="https://twitter.com" target="_blank" rel="noopener">
						<font-awesome-icon :icon="['fab', 'twitter']" />
					</a>
					<a href="https://plus.google.com" target="_blank" rel="noopener">
						<font-awesome-icon :icon="['fab', 'google-plus-g']" />
					</a>
				</div>
			</div>

			<!-- line -->
			<div class="h-[2px] bg-white/30"></div>

			<!-- bottom part -->
			<div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center mt-8">
				<div>
					<ul class="flex flex-wrap justify-center md:justify-start items-center gap-4">
						<li>
							<a href="#features">Tour</a>
						</li>
						<li>
							<a href="#features">Features</a>
						</li>
						<li>
							<a href="#pricing">Pricing Plans</a>
						</li>
						<li>
							<a href="#cta">Our Works</a>
						</li>
						<li>
							<a href="#cta">Brands</a>
						</li>
						<li>
							<a href="#contact">Contacts</a>
						</li>
					</ul>
				</div>
				<div class="flex justify-center md:justify-end items-center text-white">
					<p>© 2025. All rights reserved.</p>
				</div>
			</div>
		</div>
	</footer>
</template>

<script setup></script>
