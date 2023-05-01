<template>
    <header>
        <var-app-bar title="标题">
            <template #left>
                <var-button color="transparent" text-color="#fff" round text>
                    <var-icon name="chevron-left" />
                </var-button>
            </template>

            <template #right>
                <var-button color="transparent" text-color="#fff" round text block @click="toggleTheme">
                    <var-icon :name="name" @click="toggle" />
                    <var-icon :name="iconName" @click="toggle" />
                </var-button>

                <var-menu same-width placement="bottom">
                    <var-button color="transparent" text-color="#fff" round text>
                        <var-icon name="translate" />
                        <var-icon name="chevron-down" />
                    </var-button>

                    <template #menu>
                        <var-cell ripple>选项卡</var-cell>
                        <var-cell ripple>选项卡</var-cell>
                    </template>
                </var-menu>
            </template>
        </var-app-bar>
    </header>
</template>

<script setup>
import { ref } from 'vue'
import { StyleProvider, Themes } from '@varlet/ui'

let currentTheme = null

const name = ref('white-balance-sunny')

function toggleTheme() {
    currentTheme = currentTheme ? null : Themes.dark
    StyleProvider(currentTheme)
}

function toggle() {
    name.value = name.value === 'white-balance-sunny'
        ? 'weather-night'
        : 'white-balance-sunny'
}
</script>