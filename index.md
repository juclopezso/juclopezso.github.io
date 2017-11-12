# Home
--------------------
Estudiante de Ingeniería de Sistemas y Computación de la Universidad Nacional de Colombia, actualmente viviendo en Bogotá, Colombia. 
Desarrollador full stack junior con conocimientos en Rails, Django, Angular 4, Ionic 3.
Apasionado por el desarrollo de aplicaciones móviles.

## Contacto
--------------------
<li><a href="#">@jcamilop9</a></li>
--------------------

## Mis proyectos
--------------------
<li><a href="#">github.com/juclopezso</a></li>
--------------------

# Posts
--------------------

Acá podrán ver todos mis post relacionados con mis proyectos o mis hobbies

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
--------------------

