<template>
  <div class="accordion-body">
    Name: {{userName}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      userName: '',
      conferencename: '',
      users: [],
    };
  },
  methods: {
    getInfos() {
      function DOMScript() {
        //  Find react instance of object
        window.FindReact = function (dom) {
          for (const key in dom) {
            if (key.startsWith('__reactInternalInstance$')) {
              console.log(key);
              return dom[key];
            }
          }
          return null;
        };

        //  UserName
        const userName = FindReact(document.getElementsByClassName('userItemContents--C2UQJ')[0]);
        console.log(userName);
        console.log(document.getElementsByClassName('userItemContents--C2UQJ')[0]);

        return {
          userName,
        };
      }

      chrome.tabs.executeScript({ code: `(${DOMScript})();` }, (results) => {
        this.userName = results.userName;
      });
    },
  },
  mounted() {
    this.getInfos();
  },
};
</script>
