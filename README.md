# salary-slider

<p align="center">
<img src="https://user-images.githubusercontent.com/42354803/69659256-d22b7b00-10a3-11ea-8718-23b9a9a37ceb.gif" width="500"/>
</p>

>🎚Salary range slider component based on Vuejs.

## ✨ Features
- Switch toggles between USD and INR.
- Scale changes on toggle.
- Stylish Tooltip.

## 🎯 Props and Events
There are three props for the component: 
  * **leftptr(Number)**  : Denotes left dot value.
  * **righptr(Number)**  : Denotes right dot value.
  * **currency(String)** : Denotes currency (USD/INR).
  
  And, there are two events:
  * **changeptr**       : fired when dot values are changed.
  * **changecurrency**  : fired when currency value change by toggling.

## 🚀 Usage
   > Download the source code. <br>
   > `cd salary-slider`. <br>
   > Run `npm install .` <br>
   > Import **SalarySlider** from **path/to/folder/src/main**.
   
   ```vue
  <template>
  <div id="app">
    <SalarySlider
      :leftptr="leftptr"
      :rightptr="rightptr"
      :currency="currency"
      @changeptr="changeptr"
      @changecurrency="changecurrency"
    />
  </div>
</template>

<script>
import SalarySlider from "salary-slider/src/main";
export default {
  name: "app",
  components: {
    SalarySlider
  },
  data() {
    return {
      leftptr: 10,
      rightptr: 100,
      currency: "INR"
    };
  },
  methods: {
    changeptr(l, r) {
      this.leftptr = l;
      this.rightptr = r;
    },
    changecurrency(newCurrency) {
      this.currency = newCurrency;
    }
  }
};
</script>
  ```

## Todo-List
- [ ] Make more generic.
- [ ] Publish on npm.

## License
[MIT](https://github.com/hv7214/Salary-Slider-Component/blob/master/LICENSE)
