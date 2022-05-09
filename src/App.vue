<!-- Rendering -->

<!-- v-if, v-else-if, v-else -->
<!-- <template>
  <button @click="handler">
    Click me!
  </button>
  <h1 v-if="isShow">
    Hello?!
  </h1>
  <h1 v-else-if="count > 3">
    Count > 3
  </h1>
  <h1 v-else>
    Good~
  </h1>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
      count: 0
    }
  },
  methods: {
    handler() {
      this.isShow = !this.isShow
      this.count += 1
    }
  }
}
</script> -->

<!-- v-if에 template를 사용하는 경우, 최상위에는 사용하지 말것, 최상위 template 아래에
사용하는 template는 화면에 렌더링 되지 않는다! -->
<!-- <template>
  <button @click="handler">
    Click me!
  </button>
  <template v-if="isShow">
    <h1>Title</h1>
    <p>Paragraph1</p>
    <p>Paragraph2</p>
  </template>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
      count: 0
    }
  },
  methods: {
    handler() {
      this.isShow = !this.isShow
      this.count += 1
    }
  }
}
</script> -->

<!-- v-show: 연결된 데이터의 true, false와 관계없이 렌더링 한다.
display: none의 유무로 보여준다 -->
<!-- <template>
  <button @click="handler">
    Click me!
  </button>
  <h1 v-show="isShow">
    Hello?!
  </h1>
</template>

<script>
export default {
  data() {
    return {
      isShow: false,
      count: 0
    }
  },
  methods: {
    handler() {
      this.isShow = !this.isShow
      this.count += 1
    }
  }
}
</script> -->

<!-- v-for: 숫자 데이터 필요 시 반복의 item을 소괄호로 묶고 뒤에, 를 적고 변수 선언 -->
<!-- <template>
  <ul>
    <li
      v-for="(f, i) in fruits"
      :key="f">
      {{ f }}-{{ i + 1 }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      fruits: ['Apple', 'Banana', 'Cherry']
    }
  }
}
</script> -->

<!-- 복잡한 배열 이용 -->
<!-- v-for로 배열 출력 시 배열의 아이템들을 고유하게 구분할 수 있는 특정 속성이 있어야 한다.  -->
<template>
  <button @click="handler">
    Click me!
  </button>
  <ul>
    <li
      v-for="{id, name} in newFruits"
      :key="id">
      {{ name }}-{{ id }}
    </li>
  </ul>
</template>

<script>
// `npm i -D shortid` 설치: 각각의 id를 고유하게 만들어주는 패키지
import shortid from 'shortid'

export default {
  data() {
    return {
      fruits: ['Apple', 'Banana', 'Cherry']
    }
  },
  computed: {
    newFruits() {
      return this.fruits.map(fruit => ({
          id: shortid.generate(),
          name: fruit
      }))
    }
  },
  methods: {
    handler() {
      this.fruits.push('Orange')
    }
  }
}
</script>