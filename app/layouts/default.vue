<template>
    <div class="flex min-h-screen w-full">
        <AppSidebar />

        <div class ="flex-1 flex flex-col min-w-0">
            <main>
            <slot />
            </main>
            <footer>
                <p class="text-sm text-muted text-center">
                    Vertree • © {{ new Date().getFullYear() }}
                </p>
            </footer>
        </div>
    </div>
</template>