<template>
  <div>
    <div class="robot-name">
      {{robot.head.title}}
      <span v-if="robot.head.onSale" class="sale">Sale!</span>
    </div>
    <div class="top-row">
      <div class="top part">
        <img :src="robot.head.src" title="head" />
        <button @click="selectPreviousHead()" class="prev-selector">&#9668;</button>
        <button @click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img :src="robot.leftArm.src" title="left arm" />
        <button @click="selectNextLeftArm()" class="prev-selector">&#9650;</button>
        <button @click="selectPreviousLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img :src="robot.torso.src" title="left arm" />
        <button @click="selectNextTorso()" class="prev-selector">&#9668;</button>
        <button @click="selectPreviousTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img :src="robot.rightArm.src" title="left arm" />
        <button @click="selectNextRightArm()" class="prev-selector">&#9650;</button>
        <button @click="selectPreviousRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img :src="robot.base.src" title="left arm" />
        <button @click="selectNextBase()" class="prev-selector">&#9668;</button>
        <button @click="selectPreviousBase()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';

export default {
  name: 'RobotBuilder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedRightArmIndex: 0,
      selectedTorsoIndex: 0,
      selectedLeftArmIndex: 0,
      selectedBaseIndex: 0,
    };
  },
  computed: {
    robot() {
      return {
        head: availableParts.heads[this.selectedHeadIndex],
        leftArm: availableParts.arms[this.selectedLeftArmIndex],
        rightArm: availableParts.arms[this.selectedRightArmIndex],
        torso: availableParts.torsos[this.selectedTorsoIndex],
        base: availableParts.bases[this.selectedBaseIndex],
      };
    },
  },
  methods: {
    selectNextHead() {
      /* eslint-disable operator-linebreak */
      this.selectedHeadIndex =
        (this.selectedHeadIndex + 1) % this.availableParts.heads.length;
    },
    selectPreviousHead() {
      this.selectedHeadIndex =
        this.selectedHeadIndex < 1
          ? this.availableParts.heads.length - 1
          : this.selectedHeadIndex - 1;
    },
    selectNextRightArm() {
      /* eslint-disable operator-linebreak */
      this.selectedRightArmIndex =
        (this.selectedRightArmIndex + 1) % this.availableParts.arms.length;
    },
    selectPreviousRightArm() {
      this.selectedRightArmIndex =
        this.selectedRightArmIndex < 1
          ? this.availableParts.arms.length - 1
          : this.selectedRightArmIndex - 1;
    },
    selectNextLeftArm() {
      /* eslint-disable operator-linebreak */
      this.selectedLeftArmIndex =
        (this.selectedLeftArmIndex + 1) % this.availableParts.arms.length;
    },
    selectPreviousLeftArm() {
      this.selectedLeftArmIndex =
        this.selectedLeftArmIndex < 1
          ? this.availableParts.arms.length - 1
          : this.selectedLeftArmIndex - 1;
    },
    selectNextTorso() {
      /* eslint-disable operator-linebreak */
      this.selectedTorsoIndex =
        (this.selectedTorsoIndex + 1) % this.availableParts.torsos.length;
    },
    selectPreviousTorso() {
      this.selectedTorsoIndex =
        this.selectedTorsoIndex < 1
          ? this.availableParts.torsos.length - 1
          : this.selectedTorsoIndex - 1;
    },
    selectNextBase() {
      /* eslint-disable operator-linebreak */
      this.selectedBaseIndex =
        (this.selectedBaseIndex + 1) % this.availableParts.bases.length;
    },
    selectPreviousBase() {
      this.selectedBaseIndex =
        this.selectedBaseIndex < 1
          ? this.availableParts.bases.length - 1
          : this.selectedBaseIndex - 1;
    },
  },
};
</script>

<style scoped>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
.robot-name {
  /* position: absolute; */
  text-align: center;
  top: -25px;
  width: 100%;
}
.sale {
  color: red;
}
</style>
