---
layout: site
title: Patient Review
seo_title: ડૉ. જવાદ મસાણી – દર્દીઓનો અનુભવ
seo_description: ડૉ. જવાદ મસાણી દ્વારા આપવામાં આવેલી ફિઝિયોથેરાપી સારવાર વિશે તમારો અનુભવ શેર કરો અને અન્ય દર્દીઓને માર્ગદર્શન આપો.
thumbnail: /Araogya/assets/uploads/review-cover.jpg
---

<section class="pb-20 bg-white">
  <div class="max-w-xl mx-auto px-4 sm:px-6 lg:px-8">

    <form id="reviewForm"
          class="bg-white border border-slate-200 rounded-3xl p-6 space-y-5">

      <h1 class="text-2xl font-bold text-slate-900 font-gujarati text-center mb-6 mt-8">
  ડૉ. જવાદ મસાણી દ્વારા આપવામાં આવેલી સારવારનો તમારો અનુભવ શેર કરો
</h1>

<p class="text-slate-600 text-center font-gujarati mb-10">
  તમારો સાચો પ્રતિભાવ અન્ય દર્દીઓને યોગ્ય નિર્ણય લેવામાં મદદરૂપ થશે
</p>


      <input type="text" name="name" required
        placeholder="તમારું નામ"
        class="w-full border rounded-xl px-4 py-3">

      <input type="tel" name="phone" required
        placeholder="મોબાઇલ નંબર"
        pattern="[0-9]{10}"
        class="w-full border rounded-xl px-4 py-3">

      <div class="text-center">
  <p class="mb-2 font-medium text-slate-700">Rating આપો</p>

  <div class="flex justify-center gap-2 text-3xl cursor-pointer" id="stars">
    <span data-value="1">☆</span>
    <span data-value="2">☆</span>
    <span data-value="3">☆</span>
    <span data-value="4">☆</span>
    <span data-value="5">☆</span>
  </div>

  <input type="hidden" name="rating" value="5" required>
</div>


      <textarea name="review" rows="4" required
        placeholder="તમારો અનુભવ લખો"
        class="w-full border rounded-xl px-4 py-3"></textarea>

      <label class="flex gap-2 text-sm text-slate-600">
        <input type="checkbox" required>
        હું મારા રિવ્યુને વેબસાઇટ પર બતાવવાની મંજૂરી આપું છું
      </label>

      <button type="submit"
        class="w-full bg-teal-600 text-white py-3 rounded-xl font-bold">
        Submit Review
      </button>

      <div id="successMsg"
     class="hidden mt-6 p-4 bg-green-50 rounded-xl text-center">

  <p class="text-green-700 font-bold mb-3 font-gujarati">
    🙏 તમારો પ્રતિભાવ આપવા બદલ ખૂબ આભાર!
  </p>

  <p class="text-slate-600 text-sm mb-4 font-gujarati">
    જો તમે માત્ર 30 સેકન્ડ કાઢીને Google પર પણ રિવ્યુ આપશો,
    તો તે અન્ય દર્દીઓને યોગ્ય નિર્ણય લેવા માટે ખૂબ મદદરૂપ થશે.
  </p>

  <a href="https://g.page/r/Caxb3m1VHzFbEAE/review"
     target="_blank"
     class="inline-block bg-blue-600 text-white
            px-6 py-3 rounded-lg font-bold
            hover:bg-blue-700 transition">
    ⭐ Google પર રિવ્યુ આપો
  </a>

</div>


    </form>

  </div>
</section>

<script>
document.addEventListener("DOMContentLoaded", function () {

  const form = document.getElementById("reviewForm");
  const successMsg = document.getElementById("successMsg");

  form.addEventListener("submit", function (e) {
    e.preventDefault();

    const data = {
      name: form.name.value,
      phone: form.phone.value,
      rating: form.rating.value,
      review: form.review.value
    };

    // fire-and-forget (no CORS issues)
    fetch("https://script.google.com/macros/s/AKfycbwgmeUkqpR806s4cQz3IAqh1G1baovJM1u0XRuC7rbrND5OwqGIudXX5BUo7ELhBR9gYA/exec", {
      method: "POST",
      mode: "no-cors",
      body: JSON.stringify(data)
    });

    // UX success (backend already confirmed working)
    form.reset();
    successMsg.classList.remove("hidden");
  });

});
  const stars = document.querySelectorAll("#stars span");
const ratingInput = document.querySelector("input[name='rating']");

stars.forEach((star, index) => {
  star.addEventListener("click", () => {
    stars.forEach((s, i) => {
      s.textContent = i <= index ? "★" : "☆";
    });
    ratingInput.value = index + 1;
  });
});

</script>
