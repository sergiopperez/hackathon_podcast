# PodcastNER - Hackathon SomosNLP 🤗
Transcribir podcasts en español y aplicar PLN para resumir y responder preguntas

<p align="center">
    <img src="https://media.licdn.com/dms/image/sync/D4E27AQG2xfLa3-GbSA/articleshare-shrink_800/0/1681142292131?e=1681754400&v=beta&t=p1VlImcl9P4qTskgX44fZuySo0d3Kjkkzf8zilCpXMY"  width="50%" height="20%">
</p>

## Autores 👥:
* [Sergio Pérez](https://www.linkedin.com/in/sergiopp?originalSubdomain=uk)
* [David Mora](https://www.linkedin.com/in/davidfmora/)
* [Alberto Fernández](https://www.linkedin.com/in/alberto-fernandez-hernandez-3a3474136/)

## Resumen del proyecto

<p align="center">
    <img src="./media/esquema_proyecto.png"  width="80%" height="50%">
</p>

1. Extracción de transcripciones de vídeos de YouTube. Herramientas empleadas:
    * 📚 [youtubesearchpython](https://pypi.org/project/youtube-search-python/): extracción de audio (formato .mp3)
    * 📚 [openai-whisper](https://github.com/openai/whisper): modelo transformer de "speech recognition"

2. Extracción de entidades a partir de las transcripciones anteriores. Herramientas empleadas:
    * 📚 [openai](https://pypi.org/project/openai/): obtención de entidades mediante _prompt engineering_. El modelo empleado ha sido __DaVinci003__
    ```
    Perform name entity recognition in Spanish. The classes are books, films, videogames, songs, places, dates, topics, organizations and people. 
    The output should follow the format: [{'class': 'people', 'text': "name of the person"}, {'class': 'books', 'start': 'name of the book}] 
    
    Sentence: 
    ```

3. Limpieza de las etiquetas + posterior _finetuning_. Herramientas empleadas:
    * 📚 [argilla](https://argilla.io/): re-etiquetado manual (corrección de errores)
        * 📊 __Tras el re-etiquetado, el dataset final se encuentra almacenado [en el siguiente enlace](https://huggingface.co/datasets/hackathon-somos-nlp-2023/podcasts-ner-es)__ 
    * 📚 [torch](https://pypi.org/project/torch/) + [huggingface](https://huggingface.co/): _finetuning_ del modelo Bertin-GPT-J [1]
        * [Link del modelo](hackathon-somos-nlp-2023/bertin-gpt-j-6b-ner-es)
        * [1] [Link del paper sobre el modelo Bertin-GPT-J](https://rua.ua.es/dspace/bitstream/10045/122846/1/PLN_68_01.pdf)

4. Despliegue final del modelo. Herramientas empleadas:
    * 📚 [gradio](https://gradio.app/): interfaz web para despliegue de modelos ML/DL
        * 🖥️ __La aplicación final se encuentra disponible [a través del siguiente enlace](https://huggingface.co/spaces/hackathon-somos-nlp-2023/PodcastNER-GPTJ)__