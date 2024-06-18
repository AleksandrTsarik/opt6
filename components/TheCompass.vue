<template>
  <div class="compass">
    <div class="compass__inner">
      <h2 class="compass__title title">Плюсы использования сервиса «Компас» для анализа штрафов
</h2>
      <div class="compass__list">
        <div
          v-for="(item, i) in compass"
          :key="i"
          class="compass-item">
          <div class="compass-item__img">
            <img :src="item.img" alt="">
          </div>
          <div class="compass-item__description">
            <div class="compass-item__title">{{ item.title }}</div>
            <div class="compass-item__text">{{ item.text }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      compass: []
    }
  },
  async mounted() {
    const compassNew = []
    compassNew.push(
      {
        img: (await import("@/assets/img/icon/item1.svg")).default,
        title : 'Неограниченый автопарк',
        text: 'Можно добавить неограниченное кол-во машин и водителей',
      },
      {
        img: (await import("@/assets/img/icon/item2.svg")).default,
        title : 'Сокращение затрат до 50%',
        text: 'Максимально быстро узнаете о штрафах в автоматическом режиме, тем самым у вас есть время оплатить по скидке',
      },
      {
        img: (await import("@/assets/img/icon/item3.svg")).default,
        title : 'Безопасность',
        text: 'Данные передаются в зашифрованном виде, они доступны только получателю',
      },
      {
        img: (await import("@/assets/img/icon/item4.svg")).default,
        title : 'Уведомление о погашении',
        text: 'Мы оповестим вас о том, что штраф был погашен и соответствующая запись создана в ГИС ГМП',
      },
      {
        img: (await import("@/assets/img/icon/item5.svg")).default,
        title : 'Квитанция об оплате',
        text: 'После совершения оплаты банковской картой на Вашу электронную почту придет квитанция об успешной оплате.',
      },
      {
        img: (await import("@/assets/img/icon/item6.svg")).default,
        title : 'Все история сохраняется по каждой машине',
        text: 'Вся история штрафов сохраняется по машине и водителю, позволяет анализировать статистику по штрафам',
      },
    )
    this.compass = compassNew
	},
}
</script>

<style lang="scss">
.compass {
  &__list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 35px;
    @media(max-width: 1023px) {
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }
    @media(max-width: 767px) {
      grid-template-columns: 1fr;
      gap: 10px;
    }
  }
  &__title {
    text-align: center;
    margin-bottom: 35px;
  }
}
.compass-item {
  border: solid 1px #EEEFF1;
  background-color: #FBFCFD;
  padding: 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  &__img {
    flex: 0 0 60px;
    margin-right: 15px;
  }
}
</style>