---
layout: site
title: Health Blogs
---

<section class="pb-24 bg-white">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

    <div class="mb-14 text-center">
      <h1 class="text-4xl font-bold text-slate-900 mb-3">
        Health Tips & Insights
      </h1>
      <p class="text-slate-500 font-gujarati">
        સ્વસ્થ જીવન માટે ઉપયોગી માહિતી અને વિગતવાર માર્ગદર્શન
      </p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">

      {% for post in site.posts %}

      <!-- FULL CARD CLICKABLE -->
      <a href="{{ site.baseurl }}{{ post.url }}" class="group block">

        <article
          class="bg-white border border-slate-100 rounded-3xl overflow-hidden
                 shadow-sm group-hover:shadow-md transition">

          {% if post.thumbnail %}
            <img src="{{ post.thumbnail }}"
                 class="h-48 w-full object-cover">
          {% else %}
            <div class="h-48 bg-slate-200 flex items-center justify-center text-slate-400">
              <i class="fas fa-notes-medical text-5xl"></i>
            </div>
          {% endif %}

          <div class="p-6">
            <h3
              class="text-xl font-bold mb-3 font-gujarati
                     group-hover:text-teal-600">
              {{ post.title }}
            </h3>

            <p class="text-slate-600 text-sm leading-relaxed line-clamp-3 font-gujarati">
              {{ post.excerpt | strip_html | truncate: 140 }}
            </p>

            <span
              class="mt-4 inline-block text-teal-600 font-bold text-sm uppercase">
              Read More →
            </span>
          </div>

        </article>
      </a>

      {% endfor %}

    </div>
  </div>
</section>
