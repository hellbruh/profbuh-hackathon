<template>
    <div id="app">
        <div class="error" v-if="material.length==0">
            По данной ссылке ничего не найдено, 
            либо в видео отсутствует содержательная информация.
        </div>
        <div style="display:flex; flex-direction:column; align-items:center">
        <div v-if="material.length!=0">
            <div v-for="i of material"
            :key="i.id" id="cycle">
                <img v-if="i.at(-1).includes('http')" 
                    :src="i.at(-1)"
                    class="pic">
                <div v-if="!(i.at(-1).includes('http'))"
                    class="input-group" id="inp">
                    <span class="input-group-text" id="ddd">{{i[0]}}</span>
                    <textarea class="form-control" :value="i.at(-1)" :v-model="i.at(-1)" placeholder="Оставьте поле пустым при необходимости, при обработке оно исчезнет"></textarea>
                </div>
            </div>
        </div>
        </div>
        <div class="down">
            <button type="button" @click="saveResult()" class="btn btn-primary" id="b">Сохранить</button>
        </div>
    </div>
</template>

<script>
export default {
name:'ResultAlg',
data(){
    return{
        material:[
            ['00:01', 'Всем привет'],
            ['00:1', '5 Проверяем присутствующих'],
            ['https://image.winudf.com/v2/image/Y29tLm91cmxhYmVsLmN1dGVkb2d3YWxscGFwZXJfc2NyZWVuXzBfMTUzMzQwOTk1NF8wMDU/screen-0.jpg?fakeurl=1&type=.jpg'],
            ['01:10', 'Всем пока']
        ],
        res:[],
        test: [
            ['00:01', 'Всем привет'],
            ['00:1', '5 Проверяем присутствующих'],
            ['https://image.winudf.com/v2/image/Y29tLm91cmxhYmVsLmN1dGVkb2d3YWxscGFwZXJfc2NyZWVuXzBfMTUzMzQwOTk1NF8wMDU/screen-0.jpg?fakeurl=1&type=.jpg'],
            ['01:10', 'Всем пока']
        ]

    }
},
methods:{
    saveResult(){
        for (let object of this.material){
            if(object.at(-1).length>0){
                this.res.push(object)
            }
        }
        console.log(this.res)
    }
    },

}

</script>

<style scoped>
#app{
    display:flex;
    flex-direction:column;
    align-items: center;
    width:40%;
}
.error{
    width:100%;
    margin-top:40px;
    font-family:'Roboto',sans-serif;
    font-weight:100;
    font-size:24px;
    text-align:center;
}
.pic{
    filter: alpha(Opacity=91);
    opacity: 0.91;
    width:100%;
    margin-top:20px;
    margin-left:-4px;
}
#cycle{
    display:flex;
    justify-content:center;
}

#ddd{
    width:80px;
    text-align: center;
}
#inp{
    margin-top:20px;
    display:flex;
    width:100%
}
.down{
    height:150px;
    display:flex;
}
#b{
    height:40px;
    margin-top:30px;
    margin-bottom:30px;
}
</style>