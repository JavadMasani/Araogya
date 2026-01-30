---
layout: site
title: Patient Reviews
---

<section class="py-24 bg-white">
  <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">

    <div class="text-center mb-14">
      <h1 class="text-4xl font-bold text-slate-900 mb-2">
        દર્દીઓના પ્રતિભાવો
      </h1>
      <p class="text-slate-500 font-gujarati">
        સાચા અનુભવ, સાચી વાત
      </p>
    </div>

    <div class="space-y-8">

      {% for review in site.reviews %}
      {% if review.status == "approved" %}

      <div class="bg-slate-50 p-6 rounded-2xl border border-slate-100">
        <p class="text-slate-700 font-gujarati mb-4">
          “{{ review.content | strip_html }}”
        </p>
        <div class="flex justify-between items-center">
          <span class="font-bold text-slate-900">
            {{ review.name | default: "Patient" }}
          </span>
          <span class="text-yellow-400">
            {{ review.rating }}
          </span>
        </div>
      </div>

      {% endif %}
      {% endfor %}

    </div>
  </div>
</section>
