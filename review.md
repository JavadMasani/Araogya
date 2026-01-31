---
layout: site
title: Patient Review
---

<section class="pb-20 bg-white">
  <div class="max-w-xl mx-auto px-4 sm:px-6 lg:px-8">

    <form id="reviewForm"
          class="bg-white border border-slate-200 rounded-3xl p-6 space-y-5">

      <h1 class="text-2xl font-bold text-slate-900 font-gujarati text-center mb-12 mt-8">
        તમારો અનુભવ શેર કરો
      </h1>

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

  <input type="hidden" name="rating" value="★★★★★" required>
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

      <p id="successMsg"
         class="hidden text-green-600 text-center font-bold">
        તમારો રિવ્યુ સફળતાપૂર્વક મોકલાયો છે 🙏
      </p>

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
