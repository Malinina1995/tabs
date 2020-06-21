<template>
    <div id="app">
        <tabs ref="tabs" @indexChanged="indexChangedHandler">
            <tab name="Корпоративные ценности" :selected="true">
                <h1>Корпоративные ценности</h1>
                <div>
                    <p>Оцените, соответсвует ли поведение сотрудника орпторативным ценностям Х5</p>
                    <card title="1. Честность и порядочность">
                        <item
                                title="Соблюдает договоренности"
                                :values="values"
                                v-model="selectedData.first"
                        />
                        <item
                                title="Дает коллегам информацию"
                                v-model="selectedData.second"
                                :values="values"/>
                        <item
                                title="Абсолютно нетерпим к коррупции"
                                v-model="selectedData.third"
                                :values="values"/>
                    </card>
                </div>
            </tab>
            <tab name="Корпоративные компетенции">
                <h1>Корпоративные компетенции</h1>
            </tab>
            <tab name="Профессиональные навыки">
                <h1>Профессиональные навыки</h1>
            </tab>
            <tab name="Предварительное решение об итоговой оценке">
                <h1>Предварительное решение об итоговой оценке</h1>
            </tab>
            <tab name="Завершение оценки">
                <h1>Завершение оценки</h1>
            </tab>
        </tabs>
        <button v-if="prevIsVisible" @click="prev()">Prev</button>
        <button @click="next()">Next</button>
        <button @click="save()">Сохранить</button>
    </div>
</template>

<script>
    import Tabs from './components/Tabs.vue'
    import Tab from "./components/Tab";
    import Item from "./components/item";
    import Card from "./components/card";

    export default {
        name: 'App',
        components: {
          Card,
            Item,
            Tabs,
            Tab
        },
        data() {
            return {
                selectedIndex: 0,
                selectedData: {
                    'first': null,
                    'second': null,
                    'third': null
                },
                values: [
                    {title: 'нет', value: '0'},
                    {title: 'да, с исключениями', value: '1'},
                    {title: 'да, полностью', value: '2'},
                ],
                saveInfo: {}
            }
        },
        computed: {
            prevIsVisible() {
                return !!this.selectedIndex
            }
        },
        methods: {
            prev() {
                this.$refs.tabs.prev()
            },
            next() {
                this.$refs.tabs.next();
                console.log(this.selectedData)
            },
            indexChangedHandler(index) {
                this.selectedIndex = index
            },
            save() {
                this.saveInfo = {...this.selectedData}
                console.log(this.saveInfo)
            }
        }
    }
</script>

<style>
    ul {
        display: flex;
        justify-content: space-around;
    }
</style>
