# Распространенные ошибки в css-bliss

** Примечание: ** Некоторые из них имеют смысл, только если вы читаете их по порядку, потому что они основаны на предыдущем.

# Несколько модулей применяются к одному тегу

### Плохо

    <div class="PriceWidget">
      <button class="PriceWidget-submit Button">Пересчитать</button>
    </div>
      
### Хорошо

    <div class="PriceWidget">
      <div class="PriceWidget-submit">
        <button class="Button">Пересчитать</button>
      </div>
    </div>

**или**

    <div class="PriceWidget">
      <button class="Button Button--recalculate">Пересчитать</button>
    </div>
    
# Классы модуля и элемента применяются к одному тегу

### Плохо

    <div class="PriceWidget PriceWidget-submit">
      <button class="Button">Пересчитать</button>
    </div>
      
### Хорошо

    <div class="PriceWidget">
      <div class="PriceWidget-submit">
        <button class="Button">Пересчитать</button>
      </div>
    </div>
    
# Ширина применяется на уровне модуля

### Плохо

    .Button {
      width: 60px;
    }
  
### Хорошо

    .PriceWidget-submit {   // оборачивает кнопку
      width: 60px;
    }
    
# Внешние отступы применяются на уровне модуля

### Плохо

    .Button {
      margin-left: 10px;
    }
  
### Хорошо

    .PriceWidget-submit {   // оборачивает кнопку
      padding-left: 10px;
    }  

# Ширина применяется к модификатору модуля

Хотя css-bliss явно не запрещает делать это, его, как правило, следует избегать. Всякий раз, когда вы обнаружите, что используете `width` в Модификаторе модуля, рассмотрите возможность применения` width` вместо родительского элемента.

### Не так хорошо, как хотелось бы

    .Button--width60px {
      width: 60px;
    }
  
### Хорошо

    .PriceWidget-submit {   // оборачивает кнопку
      width: 60px;
    }
    
# Внешние отступы применяются к модификатору модуля

Хотя css-bliss явно не запрещает делать это, его, как правило, следует избегать. Чрезмерное использование внешних отступов плохо для модульности. Всякий раз, когда вы обнаружите, что используете `margin`, попробуйте вместо этого использовать `padding` для родительского элемента.

### Не так хорошо, как хотелось бы

    .Button--margin10px {
      margin: 10px 0;
    }
  
### Хорошо

    .PriceWidget-submit {   // оборачивает кнопку
      padding: 10px 0;
    }
