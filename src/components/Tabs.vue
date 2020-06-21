<template>
    <div>
        <div class="tabs">
            <ul>
                <li v-for="(tab, index) in tabs" :key="tab.name" :class="{ 'is-active': tab.isActive }">
                    <a :href="tab.href" @click="selectTab(index)">{{ tab.name }}</a>
                </li>
            </ul>
        </div>

        <div class="tabs-details">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Tabs',
    data() {
        return {
            tabs: []
        };
    },

    created() {
        this.tabs = this.$children;
    },
    methods: {
        selectTab(selectedIndex) {
            this.tabs.forEach((tab, index) => {
                tab.isActive = (index === selectedIndex);
            });
            this.$emit('indexChanged', selectedIndex)
        },
        prev(){
            const index = this.getSelectedIndex();
            if(index){
                this.selectTab(index - 1);
            }
        },
        next(){
            const index = this.getSelectedIndex();
            if(index + 1 < this.tabs.length){
                this.selectTab(index + 1);
            }
        },
        getSelectedIndex(){
            const tab = this.tabs.find(tab => tab.isActive);
            return this.tabs.indexOf(tab);
        }
    }
}
</script>

<style scoped>

</style>
