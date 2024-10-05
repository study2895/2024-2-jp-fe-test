<template>
  <div class="page-background">
    <div class="page-content">
      <Header
        :isGyeonggiToSeoul="isGyeonggiToSeoul"
        :initialSearchQuery="searchQuery"
        @toggle-route="toggleRoute"
      />
      <div class="search-results">
        <div class="result-header">
          <span>{{ isGyeonggiToSeoul ? '경기' : '서울' }}</span>
        </div>
        <BusItem
          v-for="(bus, index) in filteredBuses"
          :key="index"
          :number="bus.routeName"
          :route="bus.regionName"
          :isActive="selectedBus === bus.routeId"
          @select="selectBus(bus.routeId)"
        />
      </div>
      <Footer />
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import Header from './Header.vue'
import Footer from './Footer.vue'
import BusItem from './BusItem.vue'

const route = useRoute()

const isGyeonggiToSeoul = ref(true)
const searchQuery = ref('')

// buses가 데이터로 설정되는 부분
onMounted(() => {
  searchQuery.value = route.query.q || ''
  isGyeonggiToSeoul.value = route.query.direction === 'gyeonggi-to-seoul'

  // route.state가 undefined일 수 있으므로 기본값 설정
  buses.value = route.state?.results || []
  console.log('검색 결과 buses: ', buses.value) // 콘솔에 출력해서 데이터 확인
})

const selectedBus = ref(null)
const buses = ref([])

const toggleRoute = (value) => {
  isGyeonggiToSeoul.value = value
}

const selectBus = (busId) => {
  selectedBus.value = busId
}

const filteredBuses = computed(() => {
  return buses.value.filter((bus) => bus.routeName.includes(searchQuery.value))
})
</script>

<style scoped>
@import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css');

body {
  font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Helvetica, Arial, sans-serif;
}

.page-background {
  background-color: #f5f5f5;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  padding: 0 16px;
}

.page-content {
  max-width: 414px;
  width: 100%;
  min-width: 320px;
  background-color: #ffffff;
  color: #5b5b5b;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  padding: 0 24px;
  position: relative;
  overflow: hidden;
}

.search-results {
  margin-top: 0;
}

.result-header {
  background-color: #f9f6f6;
  margin-left: -24px;
  margin-right: -24px;
  padding: 4px 24px;
  font-size: 14px;
  font-weight: 500;
  color: #5b5b5b;
  margin-bottom: 12px;
}

@media (max-width: 414px) {
  .page-background {
    padding: 0;
  }

  .page-content {
    box-shadow: none;
  }
}
</style>
