---
---
<!DOCTYPE html>
<html lang="gu">
<head>
  <meta charset="UTF-8">
  <title>આરોગ્ય માર્ગદર્શન</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Tailwind + Fonts (same as index) -->
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Gujarati:wght@400;700&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

  <style>
    body { font-family: 'Poppins', 'Noto Sans Gujarati', sans-serif; }
  </style>
</head>

<body class="bg-white text-slate-800">

<section class="py-24 bg-white">
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

      <article
        class="bg-white border border-slate-100 rounded-3xl overflow-hidden shadow-sm hover:shadow-md transition">

        {% if post.thumbnail %}
          <img src="{{ post.thumbnail }}"
               alt="{{ post.title }}"
               class="h-48 w-full object-cover">
        {% else %}
          <div class="h-48 bg-slate-200 flex items-center justify-center text-slate-400">
            <i class="fas fa-notes-medical text-5xl"></i>
          </div>
        {% endif %}

        <div class="p-6">
          <h3
            class="text-xl font-bold mb-3 font-gujarati hover:text-teal-600">
            {{ post.title }}
          </h3>

          <p class="text-slate-600 text-sm line-clamp-3 font-gujarati">
            {{ post.excerpt | strip_html | truncate: 140 }}
          </p>

          <a href="{{ site.baseurl }}{{ post.url }}"
             class="mt-4 inline-block text-teal-600 font-bold text-sm uppercase">
            Read More →
          </a>
        </div>

      </article>

      {% endfor %}

    </div>
  </div>
</section>
</body>
</html>
