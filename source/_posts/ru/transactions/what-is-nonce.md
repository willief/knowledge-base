---
title: "Что такое Nonce-число?"
date: 2018-06-01 00:08:00
tags:
  - временный номер
categories:
  - 
    - transactions
primary_category: transactions
primary_category_display_name: "Транзакции"
alias:
  - ru/transactions/what-is-nonce.html
---

# __Что такое Nonce-число?__
###### {% read_time title "What is Nonce?" %} минимальное считывание
***

В Ethereum каждая транзакция имеет одноразовый номер, называемый Nonce. Nonce - это количество транзакций, отправленных с данного адреса.

В английском языке nonce - это число, которое можно использовать только один раз. В криптографии "nonce" - это одноразовый код, выбранный произвольным или псевдо-произвольным способом, который используется для безопасной передачи главного пароля, предотвращая атаки с использованием перехваченных записей.

Каждый раз, когда вы отправляете транзакцию, значение одноразового номера увеличивается на `1`. Существуют правила о том, какие транзакции считаются действительными транзакциями, и одноразовый номер используется для обеспечения соблюдения некоторых из этих правил. В частности:

* **Транзакции должны идти по порядку.** Транзакция с нонсом `1` не может быть замайнена раньше транзакции с нонсом `0`.

* **Никаких пропусков!** Ваша транзакция с нонсом `2` не может быть замайнена, если вы еще не отправили транзакции с нонсами `1` и `0`.



## __Почему это имеет значение?__

Это значение предотвращает двойные расходы, поскольку одноразовый номер всегда будет указывать порядок транзакций. Если двойное расходование _все же_ происходит, то обычно вследствие следующего процесса:

* Транзакция отправляется одной стороне.
* Сторона ждет ее регистрации .
* Что-то получено от этой первой транзакции.
* Быстро отправляется другая транзакция с высокой ценой на газ.
* Вторая транзакция получается первой, таким образом делая недействительной первую транзакцию.

Вот почему биржи ждут, чтобы вы получили определенное количество подтверждений, прежде чем разрешить вам торговать недавно внесенными средствами.



## __При использовании блокчейна Ethereum вышесказанное невозможно.__

В Ethereum этот метод "двойных трат" невозможен, поскольку в каждую транзакцию включен одноразовый номер. Даже если вы попытаетесь выполнить вышеизложенное, это не сработает, поскольку вторая транзакция (одноразовый номер `3`) не может быть получена до первой транзакции (одноразовый номер `2`).