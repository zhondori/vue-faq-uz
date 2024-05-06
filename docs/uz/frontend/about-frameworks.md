# Frontend freymvorklar haqida

::: details "reaktivlik" nima?

Ehtimol, frontend dasturi va backend dasturi, mikroservis yoki hatto GUI ilovasi o'rtasidagi eng asosiy farq bu "**reaktivlik**" tushunchasi.

Bekend tomonda ishlaganda, dasturchi ma'lumotlar oqimini qanday boshqarishi aniqroq. U uni qayerdan olish, qayerga jo‘natish, kim o‘zgartirishi mumkinligini belgilash, bularning barchasi bitta thread yoki multithread tizimda

Front tomonda UI interaktivlik omili katta rol o'ynaydi - ma'lumotlar foydalanuvchiga dinamik ravishda ko'rsatilishi kerak, foydalanuvchi ma'lumotlarni o'zgartirishi mumkin, ma'lumotlarni turli pudratchilar (foydalanuvchi, backend, ichki hisoblar) o'zgartirishi mumkin. Printsipial jihatdan, oddiy backend'dagi kabi dasturlash yondashuvlaridan foydalanish mumkin, ya'ni har bir joyda ma'lumotlar o'zgarishini o'zingiz kuzatib borasiz va barcha o'zgarishlarni qo'lda amalga oshirasiz. Bu juda ko'p boilerplate - muntazam, takrorlanadigan kodga olib keladi. Reaktiv freymvorklar o'zgaruvchilar o'zgarganda yangilanishi avtomatik bajarib, dasturchilar uchun hayotni ancha osonlashtirdi.

Reaktiv freymvorklarda reaktiv o'zgaruvchini yaratish va u, masalan, input'ning qiymati ekanligini ko'rsatish kifoya. Foydalanuvchi ushbu maydonga qiymat kiritganda, o'zgaruvchi avtomatik ravishda yangilanadi va unga bog'liq bo'lgan barcha boshqa o'zgaruvchilar ham yangilanadi. Buning uchun qo'shimcha kod yozishingiz shart emas.

Oddiy qilib aytganda, reaktiv o'zgaruvchi oddiy o'zgaruvchiga nisbatan proksi'ga o'ralgan bo'lib, uning o'zgarishlarini kuzatib boradi va o'zgaruvchi o'zgarganda xabardor qilinishi kerak bo'lgan barcha narsalarni qiymatni qayta hisoblashi uchun qayta chaqirib yuboradi.

:::

::: details Qanday reaktiv frontend freymvorklar mavjud?

React, Vue, Angular eng keng tarqalganlari. Yana ko'p boshqa freymvorklar bor lekin uncha mashhur emas

Angular odatda yirik loyihalar (turli darajadagi dasturchilarning katta guruhlari) uchun ishlatiladi va ishlab chiqish jarayonini o'z qoidalariga mahkam bog'laydi.

React va Vue moslashuvchan va o'xshash, lekin orasida sezilarli darajada farq bor.

Vue tez, hajmi kichikroq, samaraliroq, HTML va JS'ni aralashtirib yubormaydi, o'rganishga osonroq. Faol rivojlanyapti.

React'ni orqasida - Zukerberg va keng tarqalganligi. Vakansiyalar ko'p, lekin vakansiyaga topshiruvchilar.

:::

::: details Nega Vue?

To be able to develop and manage large complex software systems, OOP - object-oriented programming - was invented, where new entities - objects - were introduced to hierarchize complexity. They encapsulated data and behavior (logic).

On the frontend, the situation is a bit different due to the presence of code in several programming languages - HTML, CSS, JavaScript. And in this case, the SFC components in Vue serve perfectly to break down the complexity of the system. Each component encapsulates the HTML template, its styling and logic.

Vue does this much better than the same React, which lumps everything together. In this aspect, Vue is unequivocally the flagship of component-oriented programming (COP) on the frontend.

In addition, Vue 3 introduced reactivity beyond components - `ref` and `reactive` variables can be set in a simple `js` module. This is used in `composable` functions. It has become possible to separate not only the reactive service (`useI18n`, `useScreenSize` for example) but also the business logic (`useShoppingCart`, `useNewsWidget`) from the view. This allows to use [MVC pattern](https://ru.wikipedia.org/wiki/Model-View-Controller) on the frontend, where the roles of `View` and partially `Controller` are performed by components responsible mainly for visualization, and the logic and model (`Model` and partially `Controller`) fall on composable functions and their reactive state.

This makes it possible to make, for example, changing the site design or replacing the UI library a much easier task.

This feature also makes Vue stand out from other reactive frameworks.

The Reactivity API in Vue 3 may not be perfect yet (which is why creator of the Vue.js Evan You has been experimenting with Reactivity Transform), but it's already quite suitable for developing large, robust, scalable systems, which was not the case with Vue 2.

::: tip
Vue's reactivity can be used without UIs at all. For example, [this VS Code extension](https://github.com/soerenuhrbach/vscode-deepl/blob/main/src/state.ts) uses the Vue 3 elements `reactive`, `ref`, and `watch` to organize reactivity in code without visual components.

:::

::: details Vue, React yoki Svelte bajara olmaydigan nima qila oladi?

Vue reaktiv ma'lumotlar bilan samaraliroq ishlaydi.

Massviga yangi element qo'shish:

```js
// React
setSomeArr([...someArr, newItem]);

// Svelte
someArr = [...someArr, newItem];

// Vue
someArr.value.push(newItem.value);
```

ES6 native proksi obyektidan foydalanish massivni yoyib yuborish va oraliq massiv yaratishdan saqlaydi. Bundan tashqari, u yanada tezroq ishlaydi.
:::
