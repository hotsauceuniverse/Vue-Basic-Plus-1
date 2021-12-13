<template>
  <h1>{{ count }}</h1>
</template>

<script>
export default {
  data() {
    return {
      count: 2
    }
  },

  // 아래는 작성하는 순서에는 상관이 실행되는 순서는 항상 같다.

  beforeCreate() { 
    // beforeCreate라는 라이프사이클은 component가 생성되기 직전에 실행되는 라이프사이클이여서 데이터가 아직 정의되기 전에 실행되는 구조이다.
    console.log('beforeCreate', this.count) //=> beforeCreate, undefined
  },
  created() { 
    // vue파일이라는 하나의 component를 초기화하는 과정에서 created라는 컴포넌트가 생성된 직후에 그 함수의 내용이 실행되는 구조이다. 
    // component가 생섣된 직후에 실행되는 것 이기 때문에 HTML구조에 연결이 되기 전 상태이다.
    console.log('Created', this.count) //=> Created, 2
    console.log(document.querySelector('h1')) //=> null
  },
  beforeMount() { 
    // beforeMount는 HTML과 연결이 되기 전 상태이기 때문에 HTML구조를 검색할 수 없다.
    console.log('beforeMount') //=> beforeMount 
    console.log(document.querySelector('h1')) //=> null
  },
  mounted() { 
    // mounted는 화면에 component가 출력이 되서 숫자 데이터가 화면에 나오고 나서 실행이 된다.
    console.log('Mounted') //=> Mounted
    console.log(document.querySelector('h1')) //=> <h1>2</h1>
  },
}
</script>
