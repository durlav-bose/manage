<template>
  <div>
    <h1>Books</h1>

    <p>Click on the book name to know author's name :</p>

    <ul>
      <li
        v-for="(list,index) in smallList"
        :key="index"
      >
        {{list.name}} is {{list.value}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lists:[
        {
          id: 1,
          name: "Ifat",
          value: "cto",
        },
        {
          id: 2,
          name: "swadhin",
          value: "ceo",
        },
        {
          id: 3,
          name: "Sudipto",
          value: "swe",
        },
        {
          id: 4,
          name: "Prapti",
          value: "swe",
        },
        {
          id: 5,
          name: "Durlav",
          value: "swe",
        },
        {
          id: 1,
          name: "Ifat",
          value: "cto",
        },
        {
          id: 2,
          name: "swadhin",
          value: "ceo",
        },
        {
          id: 3,
          name: "Sudipto",
          value: "swe",
        },
        {
          id: 4,
          name: "Prapti",
          value: "swe",
        },
        {
          id: 5,
          name: "Durlav",
          value: "swe",
        },
        {
          id: 1,
          name: "Ifat",
          value: "cto",
        },
        {
          id: 2,
          name: "swadhin",
          value: "ceo",
        },
        {
          id: 3,
          name: "Sudipto",
          value: "swe",
        },
        {
          id: 4,
          name: "Prapti",
          value: "swe",
        },
        {
          id: 5,
          name: "Durlav",
          value: "swe",
        },
      ]
    }
  },
  computed: {
    smallList() {
      let obj = {};
      let arr = [];
      this.lists.forEach((item) => {
        if(!obj[item.name]) {
          arr.push({ name: item.name, value: item.value });
          obj[item.name] = true;
        }
      })
      return arr;
    }
  },
  methods: {
    showDetails(e,num) {
      console.log(e.target.id);

      let bookauthor = e.target.getAttribute("data-book-author");
      console.log(bookauthor);
      // alert(book.innerHTML + " is written by " + bookauthor + ".");
    },
  },
};
</script>

<style>
</style>