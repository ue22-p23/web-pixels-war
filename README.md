# ue22-pixel-war

Sujet de TP aux Mines de Paris, ue22-p23.

Remplir les TODO dans le js, puis dans le css.

## l'API

Voici ce que l'API permet de faire:

* `https://pixels-war.oie-lab.net/api/v1/{map_id}/preinit`  
  pour obtenir une clef pour apeller l'init  
  * Contenu de la reponse:  
    `{"key": "some_key"}`
* `https://pixels-war.oie-lab.net/api/v1/{map_id}/init?key={some_key}`  
  pour obtenir - entre autres - toute la map; vous recevrez aussi un `user_id`, que vous allez repasser ensuite à la même fonction.  
  * Contenu de la reponse:  
    `{"id": "user_id", "nx":100, "ny":100, "data":[[...]]}`
* `https://pixels-war.oie-lab.net/api/v1/{map_id}/deltas?id={user_id}`  
  et qui cette fois va vous répondre, non pas toute la map, mais la liste des pixels qui ont changé depuis la dernière fois que cet identifiant-là a émis cet appel.  
  * Contenu de la reponse:  
    `{"id": "user_id", "nx": 100, "ny": 100, "deltas": [[...]]}`
* `https://pixels-war.oie-lab.net/api/v1/{map_id}/set/{user_id}/y/x/r/g/b`  
  pour changer la couleur du pixel en *(x, y)* avec la couleur *(r, g, b)*  
  cet appel échoue si le même id a déjà changé un pixel il y a moins de 10 secondes.  
  * Contenu de la response:  
    (json aussi) 0 si l'opération a réussi, sinon le nombre de nano-secondes à attendre avant de pouvoir peindre un pixel
