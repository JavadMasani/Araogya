---
layout: site
title: Patient Review
---

<section class="pt-28 pb-20 bg-white">
  <div class="max-w-xl mx-auto px-4 sm:px-6 lg:px-8">

    <form id="reviewForm"
          class="bg-white border border-slate-200 rounded-3xl p-6 space-y-5">

      <h1 class="text-2xl font-bold text-slate-900 font-gujarati text-center">
        તમારો અનુભવ શેર કરો
      </h1>

      <input type="text" name="name"
        placeholder="તમારું નામ (Optional)"
        class="w-full border rounded-xl px-4 py-3">

      <input type="tel" name="phone"
        placeholder="મોબાઇલ નંબર (Optional)"
        class="w-full border rounded-xl px-4 py-3">

      <select name="rating" required
        class="w-full border rounded-xl px-4 py-3">
        <option value="">Rating પસંદ કરો</option>
        <option value="★★★★★">★★★★★</option>
        <option value="★★★★☆">★★★★☆</option>
        <option value="★★★☆☆">★★★☆☆</option>
      </select>

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
const form = document.getElementById("reviewForm");
const successMsg = document.getElementById("successMsg");

form.addEventListener("submit", async function(e) {
  e.preventDefault();

  const data = {
    name: form.name.value,
    phone: form.phone.value,
    rating: form.rating.value,
    review: form.review.value
  };

  const res = await fetch(
  "https://script.google.com/macros/s/AKfycbwgmeUkqpR806s4cQz3IAqh1G1baovJM1u0XRuC7rbrND5OwqGIudXX5BUo7ELhBR9gYA/exec",
  {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(data)
  }
);


  if (res.ok) {
    form.reset();
    successMsg.classList.remove("hidden");
  }
});
</script>
