<template>
  <div class="map">
    <div>
      <input type="range" min="0" max="100" v-model.number="progress" v-on:change="getInput()" />
    </div>
    <div>
      progress = {{progress}} %
    </div>
    <div v-for="i in 10" class="container" :key="i">
      <div v-for="j in 10" class="waku" :key="j">
        <img class="fig-people" v-if="map[i-1][j-1]==0" src="@/assets/people.svg"/>
        <img class="fig-tree" v-if="map[i-1][j-1]==1" src="@/assets/tree1.svg"/>
        <img class="fig-tree" v-if="map[i-1][j-1]==2" src="../assets/tree2.svg"/>
        <div v-if="map[i-1][j-1]==3">
          <div>
            <img class="fig-grass" src="../assets/grass.svg"/>
            <img class="fig-grass" src="../assets/grass.svg"/>
          </div>
          <div>
            <img class="fig-grass" src="../assets/grass.svg"/>
            <img class="fig-grass" src="../assets/grass.svg"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  beforeMount: function () {
    this.renderMap()
  },
  data: function () {
    return {
      progress: 0,
      progPos: 0,
      map: [
        [1, 2, 1, 2, 1, 2, 1, 2, 1, 2],
        [2, 1, 2, 1, 2, 1, 2, 1, 2, 1],
        [1, 2, 1, 2, 1, 2, 1, 2, 1, 2],
        [2, 1, 2, 1, 2, 1, 2, 1, 2, 1],
        [1, 2, 1, 2, 1, 2, 1, 2, 1, 2],
        [2, 1, 2, 1, 2, 1, 2, 1, 2, 1],
        [1, 2, 1, 2, 1, 2, 1, 2, 1, 2],
        [2, 1, 2, 1, 2, 1, 2, 1, 2, 1],
        [1, 2, 1, 2, 1, 2, 1, 2, 1, 2],
        [2, 1, 2, 1, 2, 1, 2, 1, 2, 1]
      ],
      road: [
        [9, 0],
        [9, 1],
        [8, 1],
        [8, 2],
        [8, 3],
        [7, 3],
        [7, 4],
        [7, 5],
        [8, 5],
        [8, 6],
        [8, 7],
        [8, 8],
        [7, 8],
        [6, 8],
        [6, 7],
        [5, 7],
        [5, 6],
        [5, 5],
        [5, 4],
        [4, 4],
        [4, 3],
        [4, 2],
        [3, 2],
        [2, 2],
        [1, 2],
        [1, 3],
        [1, 4],
        [2, 4],
        [2, 5],
        [2, 6],
        [2, 7],
        [2, 8],
        [1, 8],
        [1, 9],
        [0, 9]
      ]
    }
  },
  methods: {
    getInput: function () {
      if (!isNaN(this.progress)) {
        this.progress = Number(this.progress) <= 100 ? Number(this.progress) : 100
        this.progPos = parseInt((this.progress * this.road.length) / 101)
      } else {
        this.progress = 0
        this.progPos = 0
      }
      this.renderMap()
    },
    renderMap () {
      const position = this.road[this.progPos]
      this.road.forEach((v) => {
        this.map[v[0]][v[1]] = 3
      })
      this.map[position[0]][position[1]] = 0
    }
  }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
}

.waku {
  width: 40px;
  height: 40px;
}

.fig-tree {
  width: 100%;
  height: 100%;
}

.fig-grass {
  width: 30%;
  height: 30%;
}

.fig-people {
  width: 100%;
  height: 100%;
}

</style>
