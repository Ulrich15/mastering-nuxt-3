<template>
    <div class="">
        <div class="p-12 bg-gray-100 w-full min-h-screen flex flex-col items-center">
            <div class="prose mb-12">
                <h1>
                    <span class="font-medium">
                        Course:
                        <span class="font-bold">Mastering Nuxt</span>
                    </span>
                </h1>
            </div>
            <div class="flex flex-row justify-center flex-grow">
                <div class="prose mr-4 p-8 bg-white rounded-md min-w-[20ch] max-w-[30ch]">
                    <h3>Chapters</h3>
                    <div class="space-y-1 mb-4 flex flex-col"
                      v-for="chapter in chapters"
                         :key="chapter.slug"
                    >
                      <h4>{{ chapter.title }}</h4>
                      <NuxtLink
                          :to="lesson.path"
                          v-for="(lesson, index) in chapter.lessons"
                          :key="lesson.slug"
                          :class="{
                            'text-blue-500' : lesson.path === $route.fullPath,
                            'text-gray-600': lesson.path !== $route.fullPath
                          }"
                          class="flex flex-row space-x-1 no-underline prose-sm font-normal pl-4"
                      >
                          <span>{{ index + 1 }}</span>
                          <span>{{ lesson.title }}</span>
                      </NuxtLink>
                    </div>
                </div>

                <div class="prose p-12 bg-white rounded-md w-[65ch]">
                    <NuxtPage></NuxtPage>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
  const { chapters } = useCourse();
</script>