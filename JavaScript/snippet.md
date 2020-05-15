### 长列表优化

```javascript
computed:{
   contentHeight() {
      return this.data.length * this.itemHeight + "px";
    }
},
mounted(){
   window.addEventListener("scroll", this.handleScroll, true);
    this.handleScroll();
},
methods:{


handleScroll() {
      this.$el.querySelector(
        ".el-table__body-wrapper>.el-table__body"
      ).style.height = this.contentHeight;
      const scrollTop = this.$el.querySelector(".el-table__body-wrapper")
        .scrollTop;

      this.updateVisibleData(scrollTop);
    },
    updateVisibleData(scrollTop) {
      scrollTop = scrollTop || 0;

      const visibleCount = Math.ceil(
        (this.table_height - 36) / this.itemHeight
      );

      const start = Math.floor(scrollTop / this.itemHeight);
      const end = start + visibleCount;
      this.visibleData = this.data.slice(start, end);

      // 找到高亮的index
      let light_index = this.data.findIndex((value, index, attr) => {
        return value.gateway_id === this.gw.gateway_id;
      });

      if (light_index <= end && light_index >= start) {
        console.log("light_index", light_index, start, end);
        this.$refs.classForm.setCurrentRow(this.data[light_index]);
      }

      this.$el.querySelector(
        ".el-table__body>tbody"
      ).style.webkitTransform = `translate3d(0, ${start *
        this.itemHeight}px, 0)`;
    }
}
```
