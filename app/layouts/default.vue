<template>
    <div class="flex h-full w-full overflow-hidden">
        <AppSidebar />

        <div class ="flex-1 flex flex-col min-w-0 h-full">
            <main class="flex-1 flex-col min-h-0 overflow-y-auto">
                <slot />
            </main>
            <footer class="shrink-0 p-2 border-none">
                <p class="text-sm text-muted text-center">
                    Vertree • © {{ new Date().getFullYear() }}
                </p>
            </footer>
        </div>
    </div>
</template>