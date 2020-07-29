
<script>
import {Line} from 'vue-chartjs';
    export default {
        extends: Line,

        data(){
            return{
                url: '/products',
                year: [],
                name: [],
                price: [],
                data: ''
            }
        },

        methods:{

                getProducts(){
                    axios.get(this.url)
                    .then((response) =>{
                       this.data = response.data;
                       if(this.data){
                           this.data.forEach(element => {
                               this.year.push(element.year);
                               this.name.push(element.name);
                               this.price.push(element.price);
                           });

                           this.renderChart({
                               labels: this.year,
                               datasets: [
                                   {
                                       label:'Sales',
                                       backgroundColor: '#f87979',
                                       data: this.price
                                   }
                               ]
                           }, {responsive: true, maintainAspectRatio: false })

                       }else{
                              console.log('Could not fetch data')
                       }
                    })
                }
        },

        mounted() {
           this.getProducts();
        }
    }
</script>
