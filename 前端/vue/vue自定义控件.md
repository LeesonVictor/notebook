# vue自定义控件

标签： vue 自定义控件

---

```vue

<!--弹窗多选控件-->
<template>
  <cell
    style="min-height:3em"
    primary="content"
    value-align="left"
    :title="title"
    is-link
    @click.native="handleCellClick"
    :disabled="disabled"
  >
    <p class="cellText">{{checked_list|arrToString|keysToValuesConverter(options)}}</p>
    <div v-transfer-dom>
      <popup v-model="isPopVisible" :popup-style="{zIndex: 505,'border-top':'1px solid #E1E1E1','max-height':'80%'}">
        <div>
          <checker
            v-model="checked_list"
            @on-change="selectedChanged"
            type="checkbox"
            class="popupChecker"
            default-item-class="checker-item"
            selected-item-class="checker-item-selected"
          >
            <checker-item v-for="item in options" :key="item.key" :value="item.key">{{item.value}}</checker-item>
          </checker>
        </div>
      </popup>
    </div>
  </cell>
</template>

<script>
const COMPONENT_NAME = "PopupChecker";
import { Cell, Popup, Checker, CheckerItem } from "vux";
export default {
  name: COMPONENT_NAME,
  components: { Cell, Popup, Checker, CheckerItem },
  props: {
    value: {//对应v-model
      type: Array,
      default: []
    },
    options: {
      type: Array,
      default: []
    },
    title: {
      type: String,
      default: null
    },
    disabled: {
      type: Boolean,
      default: false
    },
    isPopShow: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      checked_list: [],
      isPopVisible: false
    };
  },
  watch: {
    value(val) {
      this.checked_list = val;
    },
    isPopShow(val) {
      this.isPopVisible = val;
    },
    isPopVisible(val) {
      this.$emit("update:isPopShow", val); //事件实现双向绑定
    }
  },
  methods: {
    handleCellClick() {
      if (!this.disabled) {
        this.isPopVisible = true;
      }
    },
    selectedChanged() {
      this.$emit("input", this.checked_list);//事件实现双向绑定
    }
  },
  filters: {
    arrToString(checked_list) {
      if (checked_list != null) {
        return checked_list.join(",");
      } else {
        return "";
      }
    }
  }
};
</script>
 <style lang="less" scoped>
.cellText {
  width: 100%;
  height: auto;
  word-wrap: break-word;
  word-break: break-all;
  overflow: hidden;
}
.popupChecker {
  padding: 0.5em;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: center;
  align-content: center;
  > * {
    flex: auto;
    margin: 0.5em 1em;
    text-align: center;
  }
}
.checker-item {
  background-color: #ddd;
  color: #222;
  font-size: 14px;
  padding: 5px 10px;
  margin-right: 10px;
  line-height: 18px;
  border-radius: 15px;
}
.checker-item-selected {
  background-color: #ff3b3b;
  color: #fff;
}
</style>


```




