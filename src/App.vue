<template>
  <div id="app">
    <div class="program-selection">
      <div class="program-selection__subscription">
        <div class="subscription__header">
          <h2>Выберите вариант для себя</h2>
        </div>
        <div class="subscription__body">
          <form name="subscription">
            <div class="subscription subscription__one-time">
              <input type="radio" id="subscription-one-time" name="subscription" value="one-time" v-model="firstSubscription">
              <label class="subscription-label" for="subscription-one-time">Разовые услуги</label>
              <label v-if=" firstSubscription !== 'one-time'" class="subscription-label-price price-one-time" for="subscription-one-time">от 3 500 р</label>
              <label v-else class="subscription-label-price price-one-time" for="subscription-one-time">{{cashSum > 0 ? cashSum : 'от 3 500 р'}}</label>
            </div>

            <div class="subscription subscription__one-month">
              <input type="radio" id="subscription-one-month" name="subscription" value="one-month" v-model="firstSubscription">
              <label class="subscription-label" for="subscription-one-month">Подписка на 1 месяц</label>
              <label v-if=" firstSubscription !== 'one-month'" class="subscription-label-price price-one-month" for="subscription-one-month">9 900 р</label>
              <label v-else class="subscription-label-price price-one-month" for="subscription-one-month">{{cashSum > 0 ? cashSum : '9 900 р'}}</label>
            </div>

            <div class="subscription subscription__three-month">
              <input type="radio" id="subscription-three-month" name="subscription" value="three-month" v-model="firstSubscription">
              <label class="subscription-label" for="subscription-three-month">Подписка на 3 месяца</label>
              <label class="subscription-label-price" for="subscription-three-month">26 700 р</label>
            </div>

            <div class="subscription subscription__six-month">
              <input type="radio" id="subscription-six-month" name="subscription" value="six-month" v-model="firstSubscription">
              <label class="subscription-label" for="subscription-six-month">Подписка на 6 месяцев</label>
              <label class="subscription-label-price" for="subscription-six-month">53 400 р</label>
            </div>

          </form>
        </div>
        <div class="subscription__footer">
          <div class="subscription-btn button btn">Оформить</div>
        </div>
      </div>
      <div v-if=" firstSubscription === 'one-time'" class="program-selection__service program-selection__one-time">
        <div class="service-selection service-selection__one-time">
          <h3>Выберите услугу</h3>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Разовая консультация нутрициолога</h4>
              <p>сбор и анализ индивидуального анамнеза, рекомендации по дополнительной диагностике, помощь в формулировке целей и этапов их достижения, анализ текущего рациона и план изменения, подбор индивидуального списка продуктов питания, советы по приготовлению продуктов и рецептам</p>
            </div>
            <div class="item__checkbox">
              <form name="one-time-consultation">
                <input type="checkbox" id="checkbox-one-time" name="one-time__checkbox" :value ="5000" v-model="cash">
                <label class="item-checkbox__label" for="checkbox-one-time">+ 5 000 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Шоппинг-сопровождение</h4>
              <p>интерактивная экскурсия с нутрициологом по магазину Азбука Вкуса (онлайн или оффлайн на выбор) с рекомендациями по выбору продуктов, состравлению индивидуальной корзины питания, чтению этикеток, сочетанию продуктов, сезонности, ингредиентам и ответами на вопросы</p>
            </div>
            <div class="item__checkbox">
              <form name="shopping-accompaniment">
                <input type="checkbox" id="checkbox-accompaniment" name="one-time__checkbox" :value="3500" v-model="cash">
                <label class="item-checkbox__label" for="checkbox-accompaniment">+ 3 500 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Индивидуальный план питания</h4>
              <p>персональный план питания на 4 недели по итогам работы в течение 1 месяца (рацион и рецепты)</p>
            </div>
            <div class="item__checkbox">
              <form name="shopping-plan">
                <input type="checkbox" id="checkbox-plan" name="one-time__checkbox" :value="8000" v-model="cash">
                <label for="checkbox-plan">+ 8 000 Р</label>
              </form>
            </div>
          </div>
        </div>
        <div class="service-selection service-selection__analyzes">
          <h3>Добавить к этому анализы</h3>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Проблемы с ЖКТ</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-problems">
                <input type="checkbox" id="checkbox-problems" name="one-time__checkbox" :value="13866" v-model="cash">
                <label for="checkbox-problems">+ 13 866 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Хочу похудеть</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-weight">
                <input type="checkbox" id="checkbox-lose-weight" name="one-time__checkbox" :value="5092" v-model="cash">
                <label for="checkbox-lose-weight">+ 5 092 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Вегетарианство</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <div class="item__checkbox-cross"></div>
              <input type="radio" id="radio-vegetarianism" name="one-time__checkbox" :value="8420" v-model="cashStyle">
              <label for="radio-vegetarianism">+ 8 420 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Спорт</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-sport" name="one-time__checkbox" :value="8934" v-model="cashStyle">
              <label for="radio-sport">+ 8 934 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Общая диагностика</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-diagnostics">
                <input type="checkbox" id="checkbox-diagnostics" name="one-time__checkbox" :value="8551" v-model="cash">
                <label for="checkbox-diagnostics">+ 8 551 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Нет энергии</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-energy">
                <input type="checkbox" id="checkbox-energy" name="one-time__checkbox" :value="14130" v-model="cash">
                <label for="checkbox-energy">+ 14 130 Р</label>
              </form>
            </div>
          </div>
        </div>
        <div class="service-selection service-selection__blood">
          <h3>Взятие крови на дому</h3>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Москва в пределах МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-moscow" name="one-time__checkbox-km" :value="1796" v-model="cashBlood">
              <label for="radio-moscow">+ 1 796 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>до 20 км от МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-mkad" name="one-time__checkbox-km" :value="4490" v-model="cashBlood">
              <label for="radio-mkad">+ 4 490 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>от 20 до 30 км от МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-mkad-over" name="one-time__checkbox-km" :value="5986" v-model="cashBlood">
              <label for="radio-mkad-over">+ 5 986 Р</label>
            </div>
          </div>
        </div>
      </div>

      <div v-else-if=" firstSubscription === 'one-month'" class="program-selection__service program-selection__one-month">
        <div class="service-selection service-selection__one-time">
          <h3>Сюда входит</h3>
          <div class="one-time__item">
            <div class="item__text item__text-big">
              <ul>
                <li>Консультация нутрициолога</li>
                <li>Сопровождение онлайн в персональном чате</li>
                <li>Рекомендации по выбору продуктов</li>
                <li>Анализ вашей продуктовой корзины</li>
                <li>Формирование новой продуктовой корзины</li>
                <li>Шоппинг-сопровождение (2 часа)</li>
              </ul>
            </div>
          </div>
        </div>
        <div class="service-selection service-selection__analyzes">
          <h3>Добавить к этому анализы</h3>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Проблемы с ЖКТ</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-problems">
                <input type="checkbox" id="checkbox-problems-month" name="one-time__checkbox" :value="13866" v-model="cash">
                <label for="checkbox-problems-month">+ 13 866 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Хочу похудеть</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-weight">
                <input type="checkbox" id="checkbox-lose-weight-month" name="one-time__checkbox" :value="5092" v-model="cash">
                <label for="checkbox-lose-weight-month">+ 5 092 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Вегетарианство</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <div class="item__checkbox-cross"></div>
              <input type="radio" id="radio-vegetarianism-month" name="one-time__checkbox" :value="8420" v-model="cashStyle">
              <label for="radio-vegetarianism-month">+ 8 420 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Спорт</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-sport-month" name="one-time__checkbox" :value="8934" v-model="cashStyle">
              <label for="radio-sport-month">+ 8 934 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Общая диагностика</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-diagnostics">
                <input type="checkbox" id="checkbox-diagnostics-month" name="one-time__checkbox" :value="8551" v-model="cash">
                <label for="checkbox-diagnostics-month">+ 8 551 Р</label>
              </form>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Нет энергии</h4>
            </div>
            <div class="item__checkbox">
              <form name="one-time-energy">
                <input type="checkbox" id="checkbox-energy-month" name="one-time__checkbox" :value="14130" v-model="cash">
                <label for="checkbox-energy-month">+ 14 130 Р</label>
              </form>
            </div>
          </div>
        </div>
        <div class="service-selection service-selection__blood">
          <h3>Взятие крови на дому</h3>
          <div class="one-time__item">
            <div class="item__text">
              <h4>Москва в пределах МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-moscow-month" name="one-time__checkbox-km" :value="1796" v-model="cashBlood">
              <label for="radio-moscow-month">+ 1 796 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>до 20 км от МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-mkad-month" name="one-time__checkbox-km" :value="4490" v-model="cashBlood">
              <label for="radio-mkad-month">+ 4 490 Р</label>
            </div>
          </div>
          <div class="one-time__item">
            <div class="item__text">
              <h4>от 20 до 30 км от МКАД</h4>
            </div>
            <div class="item__checkbox item__checkbox-custom">
              <input type="radio" id="radio-mkad-over-month" name="one-time__checkbox-km" :value="5986" v-model="cashBlood">
              <label for="radio-mkad-over-month">+ 5 986 Р</label>
            </div>
          </div>
        </div>
      </div>

<!--      <div class="modal" data-modal = "program-selection">
        <div class="modal__body animate__animated ">
          <div class="modal__window">
            <div class="modal__header">
              <div class="header__title">
                <h2 class="header-title__title">Итого по услуге</h2>
              </div>
              <div class="header__close">
                <svg class="header__icon" id="modal-program-closed">
                  <use xlink:href="spriteSvg.svg#Vector"></use>
                </svg>
              </div>
            </div>
            <div class="modal__text">
              <h3 class="program-selection__total-money"></h3>
            </div>
          </div>
        </div>
      </div>-->
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

  },
  data (){
    return {
      firstSubscription:[],
      cash:[],
      cashStyle:[],
      cashBlood:[],

    }

  },
  methods: {

  },
  computed:{
    cashSum: function () {
      return Number(this.cashStyle) + Number(this.cashBlood) + this.cash.reduce(function (sum,current){
        return sum + current;
      },0)

    }
  }

}


</script>

<style>

input[type="radio"] { display: none; }

input[type="radio"] + label:before{
  content: ' ';
  display: inline-block;
  height: 26px;
  width: 26px;
  border: 1px solid rgba(16, 74, 39, 1);
  border-radius: 50%;
  margin-right: 20px;
  background-size: 80% 80%;
  background-repeat: no-repeat;
  background-position: center center;

}

input[type="radio"]:checked + label:before{
  content: ' ';
  background-color: rgba(16, 74, 39, 1);
  background-image: url("image/service/Vector.svg") ;

}

.item__checkbox-custom input[type="radio"] + label:before{
  display: none;
}

.item__checkbox-custom input[type="radio"] + label:after{
  content: '';
  display: inline-block;
  height: 20px;
  width: 36px;
  border: 2px solid rgba(16, 74, 39, 1);
  border-radius: 50px;
  background-image: url("image/service/qewq.png");
  background-size: 50% 100%;
  background-repeat: no-repeat;
  background-position: 1px 0,6px;
  margin-left: 14px;
  background-color: rgba(196, 196, 196, 1);
}
.item__checkbox-custom input[type="radio"]:checked + label:after{
  background-color: rgba(16, 74, 39, 1);
  background-position: 15px 0,6px;
  background-image: url("image/service/qewq.png");
}

input[type="checkbox"] { display: none; }

input[type="checkbox"] + label:after{
  content: ' ';
  display: inline-block;
  height: 20px;
  width: 36px;
  border: 2px solid rgba(16, 74, 39, 1);
  border-radius: 50px;
  background-image: url("image/service/Ellipse 199.svg");
  background-size: 100% 100%;
  background-repeat: no-repeat;
  background-position: -6.5px 0,9px;
  margin-left: 14px;
}

input[type="checkbox"]:checked + label:after{
  background-color: rgba(16, 74, 39, 1);
  background-position: 7px -0.1px;
  background-image: url("image/service/Ellipse 199 (1).svg");

}

.program-selection{
  max-width: 1440px;
  height: 890px;
  margin:auto;
  display: flex;
}

.program-selection__subscription{
  width: 720px;
  height: 890px;
}

.program-selection__service{
  width: 720px;
  height: 890px;
  overflow: auto;
  margin-top: 60px;
}

.subscription__header{
  margin-top: 60px;
  margin-bottom: 70px;
}

.subscription__header h2{
  font-family:"Kudryashev Headline Sans", "Roboto",sans-serif;;
  font-size: 38px;
  font-style: normal;
  font-weight: 400;
  line-height: 40px;
  color: #222325;
  text-align: center;

}

.subscription{
  width: 560px;
  height: 110px;
  margin-left: 120px;
  display: flex;
  justify-content: space-between;
}

.subscription-btn{
  height: 60px;
  width: 266px;
  margin-left: 120px;
  font-family: "Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 16px;
  font-style: normal;
  font-weight: 700;
  line-height: 20px;

}

.subscription-label{
  font-family: "Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 600;
  line-height: 30px;
}

.subscription-label-price{
  font-family: "Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 700;
  line-height: 30px;

}

.service-selection{
  width: 500px;
  margin-left: 92px;

}
.service-selection h3{
  font-family: "Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 24px;
  font-style: normal;
  font-weight: 600;
  line-height: 30px;
  color: rgba(34, 35, 37, 1);
  margin-top: 50px;

}
.item__text h4{
  font-family:"Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: 20px;
  color: rgba(34, 35, 37, 1);
  margin-top: 30px;
}

.item__text p{
  font-family: "Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 18px;
  color:rgba(133, 140, 148, 1);
  width: 350px;
  margin-top: 10px;
}
.item__text li{
  font-family:"Proxima_Nova_Semibold","PT Sans",sans-serif;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: 20px;
  color: rgba(34, 35, 37, 1);
  margin-top: 30px;
  list-style-type: none;
  display: flex;
  justify-content: space-between;
}
.item__text li:first-child:after, .item__text li:last-child:after{
  display: inline-block;
  content: ' ';
  background-image: url("image/service/1.svg");
  background-repeat: no-repeat;
}

.item__text li:after{
  display: inline-block;
  content: ' ';
  background-image: url("image/service/checkmark.png");
  background-repeat: no-repeat;
  height: 20px;
  width: 20px;
}


.item__text-big{
  width: 500px;
}
.one-time__item{
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}
.btn {
  display: flex;
  height: 60px;
  width: 180px;
  background-color: rgba(16, 74, 39, 1);
  color: white;
  border-radius: 8px;
  align-items: center;
  justify-content: center;
  margin-top:26px;
}
.btn:hover {
  filter: drop-shadow(1px 1px 2px black);
}
.btn:active {
  box-shadow: inset 2px 2px 5px rgba(154, 147, 140, 0.5), 1px 1px 5px rgba(255, 255, 255, 1);
}
</style>
