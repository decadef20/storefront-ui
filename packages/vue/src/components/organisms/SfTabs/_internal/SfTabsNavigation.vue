<template>
  <nav class="sf-tabs-navigation">
    <slot
      :tabs="sharedState.tabs"
      :changeTab="changeTab"
      :activeTabValue="sharedState.activeTabValue"
    >
      <ul class="sf-tabs-navigation__list">
        <li
          v-for="tab in sharedState.tabs"
          :key="tab.valueComputed"
          class="sf-tabs-navigation__item"
          @click="changeTab(tab.valueComputed)"
          :class="{
            'sf-tabs-navigation__item--active':
              sharedState.activeTabValue === tab.valueComputed
          }"
        >
          <slot
            name="item"
            :tab="tab"
            :changeTab="changeTab"
            :isActive="sharedState.activeTabValue === tab.valueComputed"
          >
            <p v-text="tab.title"></p>
          </slot>
        </li>
      </ul>
    </slot>
  </nav>
</template>

<script>
export default {
  name: "SFTabsNavigation",
  inject: ["changeTab", "sharedState"]
};
</script>
