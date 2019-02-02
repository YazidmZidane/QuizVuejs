<template>
    <div>
        <b-container>
            <p>Nilai Anda = {{ nilai * 25 }}</p>
            <div role="tablist">
                <b-card v-for="(item,index) in items" no-body class="m-1" :key="item.question">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-btn v-b-toggle.collapse3  type="button" v-b-toggle="'accordion-'+ index" variant="info" v-on:click="setPosition(index)">{{ 'Soal Nomor ' + (index+1) }}</b-btn>
                    </b-card-header>
                    <b-collapse v-bind:id="'accordion-'+index" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                          <div v-if="item.btn_click">
                            <p class="card-text">{{ item.question }}</p>                            
                                <b-form-group>
                                    <b-form-radio-group v-model="item.clicked"
                                                        :options="item.answer"
                                                        name="radioInline">
                                    </b-form-radio-group>
                                </b-form-group>
                                <b-button variant="success" v-on:click="checkAnswer">Submit</b-button>
                          </div>
                          <div v-else>{{ "Sudah Dijawab" }}</div>                          
                        </b-card-body>
                    </b-collapse>
                </b-card>
            </div>
        </b-container>
    </div>
</template>
<script>
export default {
  name: 'HelloWorld',
  data: function() {
    return {      
      nilai: 0,
      position: 0,      
      items:[{
        question: '1. Nama Studio Terkaya Didunia ?',
        btn_click: true,
        clicked: String,        
        answer: [
          { text: 'Sony Picture Entertainment', value: 'a'},
          { text: 'Universal Studios', value: 'b'},
          { text: 'DC Comics', value: 'c'},
          { text: 'Ghibli Studios', value: 'd'},
        ],
        jawaban: 'b',
      },{
        question: '2. Nama OS Android Terbaru ?',
        btn_click: true,
        clicked: String,
        answer: [
          { text: 'Marshmellow', value: 'a'},
          { text: 'Nougat', value: 'b'},
          { text: 'Oreo', value: 'c'},
          { text: 'Pai Cake', value: 'd'},
        ],
        jawaban: 'c',
      },{
        question: '3. Salah Satu Platform Game Terkaya ?',
        btn_click: true,
        clicked: String,
        answer: [
          { text: 'Microsoft', value: 'a'},
          { text: 'Netease', value: 'b'},
          { text: 'Moonton', value: 'c'},
          { text: 'Tencent Holding', value: 'd'},
        ],
        jawaban: 'a',
      },{
        question: '4. Siapa Pendiri Perushaan Steam ?',
        btn_click: true,
        clicked: String,
        answer: [
          { text: 'Michael Grzesiek', value: 'a'},
          { text: 'Justin Ortiz', value: 'b'},
          { text: 'Artour Babaev', value: 'c'},
          { text: 'Gabe Newell', value: 'd'},
        ],
        jawaban: 'd',
      },],
    }    
  },
  methods: {
    setPosition(i){
        this.position = i;
            },   
    checkAnswer(){
      this.items[this.position].btn_click = false;      
      if(this.items[this.position].jawaban === this.items[this.position].clicked){this.nilai++;}
    },    
  }
}
</script>