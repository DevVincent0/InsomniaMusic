<script setup lang="ts">
import { ref } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import useSearchKeyword from '@/stores/homePage'
let searchKeyWord = ref('')
const route = useRoute()
const router = useRouter()
const SearchKeyword = useSearchKeyword()
function SearchFocus() {}
function onSubmit() {
  SearchKeyword.updateKeyword(searchKeyWord.value)
  router.push('search')
}
</script>
<template>
  <div class="fixed top-0 w-full h-70px bg-#c91317 z-100 flex items-center">
    <!-- 网站名网站logo -->
    <!-- 头部导航栏 左侧 logo-->
    <div class="w-300px flex items-center">
      <div class="w-60px ml-20px">
        <img :style="{ width: '100%' }" src="@/assets/img/logo.png" />
      </div>
      <div class="pl-20px text-20px color-#fff">Insomnia-music</div>
    </div>
    <!-- 搜索栏 -->
    <!-- 搜索 -->
    <div class="w-300px h-50px relative">
      <!-- 搜索栏 vant -->
      <van-search
        v-model="searchKeyWord"
        @focus="SearchFocus"
        @search="onSubmit"
        placeholder="请输入搜索关键词"
        background="#c61216"
        shape="round"
      />
      <!-- 热搜bang -->
      <!-- <div class="hotSearch" v-if="!searchSuggestList">
          <div class="hotSearchTitle">热搜榜</div>
            <div class="hotSearchItem"
                 v-for="(item, index) in hotSearchList"
                 :key="index"
                 @click="clickHotSearchItem(item.searchWord)">
              <div class="hotSearchIndex"
                   :class="index < 3 ? 'topThree' : ''">
                {{ index + 1 }}
              </div>
              <div class="hotSearchInfo">
                <div class="hotSearchWord"
                     :class="index < 3 ? 'hotSearchWordTopThree' : ''">
                  {{ item.searchWord }}
                </div>
                <div class="hotSearchContent">{{ item.content }}</div>
              </div>
            </div>
        </div> -->
    </div>
  </div>
</template>
