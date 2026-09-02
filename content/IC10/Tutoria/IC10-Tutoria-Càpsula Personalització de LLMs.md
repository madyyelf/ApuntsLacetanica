---
publish: true
tags:
  - apunts
---

# Llicència

Aquest document es publica sota llicència **Creative Commons 3.0 (BY - NC - SA)**

[Creative Commons 3.0 (BY - NC - SA)](https://creativecommons.org/licenses/by-nc-sa/3.0/es/legalcode.ca)

**2026 Raul Gimenez Herrada**
(raul.gimenez@lacetania.cat)

[Ko-Fi Raul Gimenez Herrada - Convida'm a un cafè!](https://ko-fi.com/raulgimenezherrada)

---

# Càpsula Personalització de LLMs

---

## LLMs locals amb Ollama

### Avantatges

- Privacitat de les dades.
- Personalització dels models.
- Models alliberats.
- No limitació de toquens.

### Desaventatges

- Rendiment.
- Maquinari.
- Muntatge.
- Manteniment.

## Fine-tuning amb Ollama

### Modelfile

Bàsicament es tracta d'afegir un arxiu amb les definicions i paràmetres que volem utilitzar per personalitzar el model.  Podem trobar la [Documentació oficial](https://docs.ollama.com/modelfile) a la pròpia web de [[Ollama]] amb tots els paràmetres possibles.

```
FROM artifish/llama3.2-uncensored:latest

SYSTEM """  
Ets un assistent que tan sols entens i parles català, si l'usuari et parla en un altre idioma idràs que no l'entens.  Les teves respostes tan sols poden ser SI o NO, binàries, sigui quina sigui la pregunta i sense més explicacions.  Si la pregunta és no binària, també respondras o bé amb SI o NO, però de forma aleatoria.  Per exemple:
- Pregunta: T'agrada el color blau? Resposta: Si.
- Pregunta: Quina és la captital de Catalunya? Resposta: Si.
- Pregunta: El verd és el color del cel? Resposta: No.
"""  
  
TEMPLATE "User: {{ .Prompt }}\nAssistant:"
```

Ara tan sols ens quedarà construïr el model i executar-lo:

- `ollama create model-finetuning -f finetuning.txt`
- `ollama run model-finetuning`

## RAG amb Ollama

## Skills?

https://chatgpt.com/c/6a4370a8-9cf0-83ed-9a3a-529991384bdd
