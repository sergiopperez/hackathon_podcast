El `get_transcriptions.ipynb` notebook toma urls de una lista de reproducción en youtube y los convierte a archivos txt procesados. El formato de los txt está pensado para ser enviado al api de OpenAI.

El `json.ipynb` notebook toma los archivos txt y manda cada frase a la api de OpenAI, junto con un prompt para que la api devuelva las name entity recognition. La respuesta se guarda en formato json. Para utilizar la api de OpenAI tenéis que crearos una cuenta y crear la key en esta página (https://platform.openai.com/account/api-keys). Te dan 5$ al crear la cuenta, y es suficiente para hacer bastantes llamadas a la api.

Prestad atención a los paths de los archivos en los notebooks, ya que tendréis que modificarlos.
