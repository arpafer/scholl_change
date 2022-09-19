# Teachers exchange school (TES)

  Todos los años los profesores que todavía no son funcionarios sino solo interinos, y que por lo tanto pueden ser cambiados de centro educativo de un año para otro, se ven en la incertidumbre de no saber si les van a asignar un centro lejos o cerca del domicilio. Por eso, la consejería de educación todos los años da la posibilidad de que profesores que estén de acuerdo en cambiar de centro rellenen un formulario y lo envíen a través de la sede electrónica de la consejería de educación. Este formulario tiene que ir firmado por los directores de ambos centros donde se intercambiaran los profesores. Incluso se ofrece la posibilidad en este formulario de que pueda haber un intercambio de 3 profesores. Es decir, por ejemplo, el profesor 1 le interesa el centro donde está el profesor 3, al profesor 3 le interesa el centro del profesor 2 y al profesor 2 le interesa el centro donde está el profesor 1.

  El problema de este proceso de intercambio es que no hay ninguna aplicación para esto. Simplemente diversas instituciones ligadas a la enseñanza, como por ejemplo el STEC, comisiones obreras, etc, ... ofrecen simples foros donde la gente escribe la información de en que centro o zona se encuentra asignada y que zona y/o isla de destino le gustaría dejando su correo electrónico o teléfono, para que otros profesores escriban si están interesados. Cada profesor que esté interesado en cambiar de centro tiene que estar mirando todos estos comentarios que deja la gente en el foro, para ver si hay alguno que le interese.
Con el prototipo de aplicación que se presenta aquí, se quiere automatizar todo este proceso, y que sea la propia aplicación quien sea capaz de encontrar y emparejar solicitudes de cambio de centro que encajen en los intereses, avisar a los respectivos profesores y que estos ya decidan y confirmen el emparejamiento si les interesa el cambio de centro. 
 
# Análisis y Requisitos

Presentamos primero un modelo de los principales conceptos que se manejan en el dominio del problema que se quiere resolver.

![PlantUML model](https://planttext.com/api/plantuml/png/VP8nJyCm48Nt-nMdZ8X4bB43YeGoT82Yj2ni9_j8B2Lsi1s4GFntKZkbQPHsofFUTy_txEJEa_Lzsm3a9_bYJMMfnPiqVS1abMKwmOrhICj5QyyaQhRdNY5xGLuPlRKLQVKTzEBu4_bXN9RyqRFp3k99PyXErCOqC1uqMdTPjagm-18rwOh7SPYbOK0dIyxzaFLezBkoBSlvBfUC67j_YbsiYvCAbvBMI5rdpIV3h0bEIexzbuXuMsiqLbLANqM6zwtOBo9lHlCnuw2lG34bG76jVm-0TTy6YJ-0k7ijRuVFyxRS5_0B81foxdXZWKZPTImKDKgIF20vQnd_nYZ-0000)



Según este modelo, la aplicación tendría registros previos de las islas, y todos los centros educativos de cada isla, así como la zona donde está cada uno. También podríamos considerar para este prototipo que los profesores también han sido registrados por la consejería de educación. A partir de aquí cada profesor empezaría a registrar su solicitud de cambio. La aplicación ya sea de manera automatizada o mediante demanda del profesor, buscaría automáticamente solicitudes de otros profesores que encajen en los intereses de intercambio de centro. Le presentaría al profesor las solicitudes que ha encontrado, y el profesor tendría la posibilidad de contactar con el otro profesor de dicha solicitud encontrada, ya sea mediante email(obligatorio en la solicitudes) o mediante teléfono, o mediante mensajes en la propia solicitud o incluso si se implementa, mediante un chat a través de la propia aplicación. A partir de aquí son ambos profesores los que se tienen que poner de acuerdo para confirmar que quieren ese intercambio de centro. Una vez que confirmen este intercambio, a los directores de ambos centros les llegaría un aviso de esta solicitud de cambio, que deberan también confirmar. Una vez que los directores también confirmen, entonces le llegaría el aviso a la consejería, la cual también debería confirmar que acepta el intercambio. En cualquiera de estas fases, la parte implicada podría denegar la solicitud. Por tanto podríamos decir que una solicitud de cambio pasa por diferentes etapas o estados. Esto lo podriamos representar por el siguiente diagrama de estados: 

![PlantUML model](https://planttext.com/api/plantuml/png/XPBF3e8m38VlVGhE9ho20OMZCJ7UY8Tcgx04HXp5g4_ld44Z5BajxU_xkdz9n-YuRsg0OdMAudWTRHqXayvlga9Rqe4kFNKCSZaGgM9pdH9oEH0xP5LD2RdytbLhpyOrf3Vt8w5FkUvVF2DL6_jAftO0G72CtPbnfBZryhdmZtc8WwGOktFTAsJJshqhqPf7MC-Jtq6Be1W84l-e0D9bVBhYUOJkmeo4hFRVw0a0)


### Casos de uso

   En lo visto hasta ahora se identifican claramente tres tipos de usuarios: los profesores, los directores y la consejería de educación. En base a estos 3 tipos de usuarios, ahora pasamos a describir los casos de uso mas importantes identificados.

   ![PlantUML model](https://planttext.com/api/plantuml/png/bP9BQiCm48RtEiKixOLp01DC8FMk3sYQ0mpIn1vGDAuUJIazVAKsqDOXDTr9ttpycXcq2H5zJ4Uh8aTBiCKW0Gn12W8JUWIBC528BAvWcwkJbmC5yHIKQlU1V0lhzwQ1zebGZ_cg2lnYD-n9H_4_K6-InfBtu0Tq_FPvLbKHQcYQ3gfR6TZLSoGf_cOx7jn-gfMgpW-V-TOJHeAT7aLi_wf7T0CzqdFAOzHp-ONf17SOCp8pDrp8Mjo1_V6AVw4RqfOTNTNLtwt2QfL3P29tJwTvCUzypKxRPAZhr59dtr6zuRBlXRY5plyPjo5dyXVx0000)


   ![PlantUML model](https://planttext.com/api/plantuml/png/dL9BRW8n3Dtx55uoY-408pH2ehEkL9K3f8aPB0MdZHFQ8cx54RWO6HYaIcoOhXo_l8zbUQd9n9Ht7X8dJxWo6XGTOTOm56-m9qryFicr7JuvaaqXaW8qQwNOuE9OrzYyax7Rqi80th2NaVi7wbos9d6GrzWRuSFr3J2xKokiwnPdUwPlf1-xDT8Jlj5NBcCesY0RZZjo-F6BwHQerOFQaVKiz7-3aVQy0KpEnFcy18LFaixni8Hk58wwgknrmM9zTjIsC7caYVwm977b42u0)

   ![PlantUML model](https://planttext.com/api/plantuml/png/hP8zJWCn48LxdsBARB4vm2fQHGgXHK9mWC5-R0PvxU2V152kb2f7oCMmOGiAXBGIdUUJtZTF8wzZuf3oQ5MIP44RZZwI0UNeQS-1oJ8DY4cygxXCshk85uJhcIk1oPgrN2zEgUun8dIqEhKjTGzWlIkZgl2RtKY0JZxyGDiQh_QxCB2JZw-tKejVUKDjszFY83WItlIEtG2wnsik1MCjzYnXXA6dTpBJgjZyxJBGLXp-IpU5PkZK_0gqN9PLVWztwyEudM9JgYdtNudJDXlqlPhVQ8vz3MVAv_a4)


 Ahora mediante los diagramas de contexto de cada tipo de usuario y en función de los casos de uso, podremos ver de una forma mas clara lo que se permite hacer en el sistema y la trazabilidad y dependencia entre ellos.

 ![PlantUML model](https://planttext.com/api/plantuml/png/fP9DJiCm48NtFiKi0IbNGBIrHID10ctvsKMZPEfOk7Qn9shlnH6u6E57B4AW1bRsUEpttdpoMMGCt6siOCEMG1hK0JS83K7j7TEUFMmn85W4JP7DyvFhcnQws64mVJFuDKKVX3WwEOOiEuNS6JPenSVwTbPUgKB9IawMysavMKZXF1Du1zQu1m406LYlZNlVHgCTz0Mv1bulYk7pLCrRGxjBvBgbHkth5fsc1Jrs_HpnW7W_p50lWmklVSTfiGfrLwdxsNnIdAjgeQvlr78rah3SaYjeDqZtnM9CBHN2B10o3Hq-tIN6TkenDEcc8t16wFo8HybybPT52YBL63x4vpkvNyHDKKgWBQdk2nh_TIdK_njWvjtQXCqV0hm0)

 ![PlantUML model](https://planttext.com/api/plantuml/png/lP51JiCm44NtFiKi0IbNG2In8P4WWIGWM4MZP4X7k7Qn7L7EnH6u6A5KGYe52aYixB7__FbFS-G3kZ3EjGWSD85a71pE4Ng2pff0os1XWGv18mpa0py_cUbJm-X7T6oXPqTTi4w8lODzYA93o0q7HYtMv-gjF5U5agsCwomfuqeAOmE1DQ3Pt0a0Y43RWStRrVDWO2h8zF0g59ljktfUCJsePJT3Cr15z-C4u5DhRjdDgKyU6y9kHiv_CsW2s_IEuDGETWpldLzcL39lyh9erNMQnSM9QYjrSQdgfatBuZYlpYP9SjCsAaupLTLRG5JFOGFaG-YV3VcCR0lQx_rtM96aRYfebosjzEM2Z4G_Ioow_fyohiFyDUCB)

 ![PlantUML model](https://planttext.com/api/plantuml/png/lL71JeGm4BttA-Qe9lo24MXrIHGKqEY9D31sgz2kROdhHtdo4_R7BBY92QwAsSHJ-sRUctalSs8TDwxlMkAaQn6evCBmZaE3K6lbSEqqhBZXq78GQ9tSlAcXwQ7lMtn0itaTwTZqDQ-7FY47HuSG1CUGAEaaRyds7MlP9KiPhMXOBA8ip2bHsY5e1QrKZmG00cYraEhZQwLGu06g1WOYcShdphoH-CpMzP8hWJa-zJwBZRMwbwR39dgXqc3jjB6_RFB9fiC3EDT2z-vJ-QD9HfCooTAAtSQBC3rZLSwkhbbHLd6MdYRvXQT4TnLDSXQNMLxiYC8QwIPHlhZ-uvRlikq8jyU26MUYM7k0iour2h8LAihjCjBSDF_bScjdRvVl)

![PlantUML model]()
  
    Se presenta ahora cada caso de uso que aparece en los diagramas de contexto como un diagrama de estados, donde se describe la conversación del usuario con el sistema, y los diferentes escenarios del caso de uso. Un escenario principal donde todo va perfectamente bien, y otros escenarios donde se describen los fallos que pudieran haber durante el transcurso del caso de uso. 
    Vamos a obviar en este prototipo los casos de uso de login, sign in y logout y a concentrarnos solo en los requisitos funcionales.

  ![PlantUML model](https://planttext.com/api/plantuml/png/XP31JiCm44Jl-nLpHigXvHPLWQ94uW95hU2243BEabWuTl4wQlaw9BuCE_HK4FN5sjtncrbVIbGXZeEbQA9br4PrGGqABOFJhFM2hGgv5XtCYmbW2wt4PyKuNHRRu5zPVC23uTsDYhhdjjdhNhcEr_m-9f8G9LnaQ2mMklT6SrKHFPuzeIWghEwQswP-hfURwwlLSbtJSMDIoOoSJmplO8rx8-1UE20SBChKIAVuDmQx5Xb2CfkOkiJNPxCt4jb1l3NQn35jUq7wntD-xBdvIDe1qllTmR988uauQQadu7cPAXnJ_y1cyC0YgkFyWdD8_AQIpAUawI-9lW40)


  ![PlantUML model](https://planttext.com/api/plantuml/png/lPJDZjCm58NtVegx1AGkPfZPHAF2G8fWGOjQs80GSftRniBnBTS9fK8y6n9FndKydPccQIaiy2R-EJx-ZXtxQQWrrqtbL6rhXv1RlMHTQIWGKCOA2h3I7Dl1i9rR1dHWTA2eQDgFWnNJ0WCnJ5RenxWUVJEbzakSufT6N9HIapUZyIZ_b5_FNZwRN4zp60o6XzIUQWJouAp_h03U1MJWD1OowP0oE3GNVG5nlb82BpRzClYkea-I6BYwCYLPWyDXxFtmw6DB5yvQpLbgdCT6XooMsIRKMBLybd7BbnXV1QU5Hyg3IYgw9juyl2zuJnvJ_O3WEJKSy8XWhAlZ3gzfRXtUxnbLshg-ARTx9_Ks-dcA_XWEP7-BsfHoE7ByNstH6xwRTZzSDyq9y5rO8OoW9llrymLn9ObkGbflY1bDJK-YpgGy5ncCwVXnXfBMkt6c61hPQkiNxGfMfj42FAvX--lj66ZdzXtgXZq8NAv3EIVDHJV83U1b1ZDx2Y3S-SVTmX3qKkujirn5tExKdw1uyvUKuQB5b7loB__5AGjS_fy5qWq_mRztnsuDVyZprl_Cn4Koah4xajrcKdGVnwDsUsBr6m00)