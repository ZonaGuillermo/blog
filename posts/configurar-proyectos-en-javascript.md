---

title: Configurar proyectos en Javascript: jsconfig.json
menu_order: 1
post_status: pending
post_excerpt: Como configurar el archivo jsconfig.json en nuestro proyecto.
taxonomy:
    category:
        - Javascript
    post_tag:
        - Javascript-configuracion
        - VSCode

---


# Configurar proyectos en Javascript: jsconfig.json

A la hora de crear un proyecto en javascript, en principio no necesitamos una configuración previa puesto que será el navegador el que interprete el código del archivo y lo ejecute. Sin enbargo, __es altamente recomendable__ ya que al realizar esta configuración podremos definir como debe comportarse nuestro proyecto. Esto es especialmente util en las siguientes situaciones:

- Cuando __trabajamos con algún framework__ como React, Vue, etc.
- Tenemos pensado __realizar testing__, ya que necesitaremos hacer configuraciones previas.
- Para un __uso de IntelliSense optimizado__ y adecuado a nuestro proyecto.
- 