<template>
  <header>
    <div class="container">
      <div class="header-wrapper">
        <ul class="header-list">
          <li><a href="#">Билеты и абонементы</a></li>
          <li><a href="#">Как купить?</a></li>
          <li><a href="#">Правила</a></li>
          <li><a href="#">Возврат билетов</a></li>
        </ul>
        <a href="#" class="header-auth"

        >
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
               class="bi bi-arrow-right-square" viewBox="0 0 16 16">
            <path fill-rule="evenodd"
                  d="M15 2a1 1 0 0 0-1-1H2a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1V2zM0 2a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V2zm4.5 5.5a.5.5 0 0 0 0 1h5.793l-2.147 2.146a.5.5 0 0 0 .708.708l3-3a.5.5 0 0 0 0-.708l-3-3a.5.5 0 1 0-.708.708L10.293 7.5H4.5z"/>
          </svg>
          <div>
            Войти
          </div>
        </a>
        <button @click="onMenuBtn" class="header-btn" :class="{active: isActiveBtn}">
          <span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "header-page",
  data() {
    return {
      isActiveBtn: false
    }
  },
  methods: {
    onMenuBtn() {
      this.isActiveBtn = !this.isActiveBtn
    }
  }
}
</script>

<style scoped>

.header-wrapper {
  display: flex;
  padding: 30px 0;
  justify-content: space-between;
  width: 100%;
  align-items: center;
}

.header-list {
  display: flex;
  flex: 1 1 0;

}

.header-list li {
  margin: 0 20px;
}

.header-list li:first-child {
  margin-left: 0;
}


.header-list a:hover {
  color: crimson;
}

.header-auth {
  background: none;
  border: none;
  color: white;
  display: flex;
  align-items: center;
  transition: all 0.3s ease;
}

.header-auth:hover{
  color: crimson;
}

.header-auth svg {
  margin-right: 10px;
}


.header-btn {
  position: relative;
  height: 25px;
  width: 35px;
  background: none;
  border: none;
  margin-left: 20px;
  cursor: pointer;
}

.header-btn:before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 2px;
  background: white;
  transform: rotate(0);
  transition: all 0.3s ease;
}

.header-btn:after {
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 100%;
  height: 2px;
  background: white;
  transform: rotate(0);
  transition: all 0.3s ease;
}

.header-btn span {
  position: absolute;
  bottom: 50%;
  transform: translateY(50%);
  right: 0;
  width: 50%;
  height: 2px;
  background: white;
  opacity: 1;
  transition: all 0.3s ease;
}

.header-btn.active:before {
  transform: rotate(45deg);
  top: 45%;
}

.header-btn.active:after {
  transform: rotate(-45deg);
  bottom: 45%;
}

.header-btn.active span {
  opacity: 0;
}

</style>