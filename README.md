# Какая embedding-модель лучше ищет код по вопросам на русском

Здесь мы проверили 63 открытые embedding-модели на одной задаче: разработчик спрашивает по-русски, а модель должна
найти в проекте кусок кода, который отвечает на вопрос. Код и имена в нём английские, комментарии бывают и
русские, и английские. Это ровно то, что происходит в RAG по коду, когда вопрос задают на русском.

## Рейтинг

Чем выше, тем лучше. «Правильный первым» показывает, в какой доле вопросов нужный кусок кода оказался на первом
месте в выдаче, «В первой пятёрке» показывает то же для первых пяти мест. MRR@10 сводит это в одно число: 1.0
значит, что правильный ответ всегда первый, 0.5 значит, что в среднем второй, 0 значит, что его нет в первой
десятке. По MRR@10 расставлены места. Последние две колонки показывают MRR@10 на двух отдельных наборах
вопросов: в одном прямо назван класс или метод, в другом спрашивают, где используется какой-то идентификатор.
Все числа усреднены по пяти языкам программирования.

| Место | Модель | Правильный первым | В первой пятёрке | MRR@10 | С именами из кода | «Где используется» | Лицензия |
|---|---|---|---|---|---|---|---|
| 1 | ai-sage/Giga-Embeddings-instruct-3B-0826 | 75% | 97% | 0.845 | 0.880 | 0.436 | MIT |
| 2 | ai-sage/Giga-Embeddings-instruct-10B-A1.8B-0826 | 74% | 97% | 0.839 | 0.869 | 0.423 | MIT |
| 3 | qwen3-embedding:8b-q8_0 (Ollama) | 67% | 93% | 0.785 | 0.841 | 0.434 | Apache-2.0 |
| 4 | qwen3-embedding:4b-fp16 (Ollama) | 67% | 93% | 0.785 | 0.852 | 0.434 | Apache-2.0 |
| 5 | qwen3-embedding:8b-fp16 (Ollama) | 67% | 93% | 0.785 | 0.844 | 0.434 | Apache-2.0 |
| 6 | qwen3-embedding:4b-q8_0 (Ollama) | 67% | 93% | 0.784 | 0.847 | 0.435 | Apache-2.0 |
| 7 | qwen3-embedding:8b-q4_K_M (Ollama) | 66% | 93% | 0.780 | 0.827 | 0.430 | Apache-2.0 |
| 8 | qwen3-embedding:4b-q4_K_M (Ollama) | 65% | 93% | 0.771 | 0.824 | 0.450 | Apache-2.0 |
| 9 | ai-sage/Giga-Embeddings-instruct | 64% | 92% | 0.761 | 0.817 | 0.415 | MIT |
| 10 | BAAI/bge-code-v1 | 65% | 91% | 0.760 | 0.868 | 0.503 | Apache-2.0 |
| 11 | codefuse-ai/F2LLM-v2-1.7B | 63% | 91% | 0.750 | 0.789 | 0.394 | Apache-2.0 |
| 12 | ai-sage/Giga-Embeddings-instruct-480M-0826 | 60% | 90% | 0.732 | 0.822 | 0.438 | MIT |
| 13 | jinaai/jina-embeddings-v5-text-small-retrieval | 60% | 90% | 0.731 | 0.819 | 0.424 | CC-BY-NC-4.0, некоммерческая |
| 14 | codefuse-ai/F2LLM-v2-4B | 61% | 90% | 0.729 | 0.747 | 0.404 | Apache-2.0 |
| 15 | perplexity-ai/pplx-embed-v2-late-0.6b (late interaction) | 61% | 88% | 0.728 | — | — | MIT |
| 16 | perplexity-ai/pplx-embed-v1-4b | 57% | 88% | 0.699 | 0.812 | 0.432 | MIT |
| 17 | jinaai/jina-embeddings-v5-text-nano-retrieval | 56% | 86% | 0.684 | 0.823 | 0.447 | CC-BY-NC-4.0, некоммерческая |
| 18 | codefuse-ai/F2LLM-v2-0.6B | 56% | 84% | 0.678 | 0.805 | 0.401 | Apache-2.0 |
| 19 | embeddinggemma:300m-bf16 (Ollama) | 53% | 84% | 0.659 | 0.747 | 0.393 | Gemma Terms of Use |
| 20 | embeddinggemma:300m-qat-q8_0 (Ollama) | 53% | 82% | 0.657 | 0.737 | 0.389 | Gemma Terms of Use |
| 21 | embeddinggemma:300m-qat-q4_0 (Ollama) | 53% | 82% | 0.657 | 0.757 | 0.378 | Gemma Terms of Use |
| 22 | jinaai/jina-code-embeddings-1.5b | 49% | 79% | 0.617 | 0.717 | 0.374 | CC-BY-NC-4.0, некоммерческая |
| 23 | Qwen/Qwen3-VL-Embedding-2B | 47% | 81% | 0.614 | 0.757 | 0.414 | Apache-2.0 |
| 24 | Qwen/Qwen3-Embedding-0.6B | 48% | 80% | 0.611 | 0.804 | 0.411 | Apache-2.0 |
| 25 | qwen3-embedding:0.6b-fp16 (Ollama) | 48% | 80% | 0.610 | 0.812 | 0.413 | Apache-2.0 |
| 26 | qwen3-embedding:0.6b-q8_0 (Ollama) | 47% | 80% | 0.608 | 0.810 | 0.413 | Apache-2.0 |
| 27 | microsoft/harrier-oss-v1-0.6b | 45% | 75% | 0.578 | 0.826 | 0.378 | MIT |
| 28 | embeddinggemma-2:270m-mxfp8-text (Ollama) | 45% | 75% | 0.576 | 0.755 | 0.317 | Gemma Terms of Use |
| 29 | embeddinggemma-2:270m-bf16-text (Ollama) | 45% | 75% | 0.575 | 0.753 | 0.310 | Gemma Terms of Use |
| 30 | perplexity-ai/pplx-embed-v1-0.6b | 44% | 75% | 0.573 | 0.805 | 0.396 | MIT |
| 31 | embeddinggemma-2:270m-nvfp4-text (Ollama) | 44% | 76% | 0.570 | 0.736 | 0.327 | Gemma Terms of Use |
| 32 | jinaai/jina-code-embeddings-0.5b | 42% | 74% | 0.554 | 0.792 | 0.366 | CC-BY-NC-4.0, некоммерческая |
| 33 | snowflake-arctic-embed2 (Ollama) | 40% | 70% | 0.528 | 0.786 | 0.423 | Apache-2.0 |
| 34 | ibm-granite/granite-embedding-311m-multilingual-r2 | 40% | 70% | 0.526 | 0.830 | 0.377 | Apache-2.0 |
| 35 | deepvk/USER-bge-m3 | 38% | 68% | 0.508 | 0.751 | 0.376 | Apache-2.0 |
| 36 | BAAI/bge-m3 | 37% | 68% | 0.505 | 0.763 | 0.391 | MIT |
| 37 | bge-m3 (Ollama) | 37% | 68% | 0.505 | 0.761 | 0.392 | MIT |
| 38 | deepvk/USER2-base | 35% | 65% | 0.478 | 0.711 | 0.414 | Apache-2.0 |
| 39 | ai-forever/FRIDA | 36% | 63% | 0.475 | 0.748 | 0.351 | MIT |
| 40 | intfloat/multilingual-e5-large-instruct | 36% | 58% | 0.454 | 0.561 | 0.349 | MIT |
| 41 | granite-embedding:278m (Ollama) | 31% | 60% | 0.431 | 0.734 | 0.359 | Apache-2.0 |
| 42 | Alibaba-NLP/gte-multilingual-base | 30% | 58% | 0.415 | 0.739 | 0.364 | Apache-2.0 |
| 43 | nomic-embed-text-v2-moe (Ollama) | 28% | 53% | 0.390 | 0.710 | 0.394 | Apache-2.0 |
| 44 | ibm-granite/granite-embedding-97m-multilingual-r2 | 28% | 52% | 0.379 | 0.800 | 0.409 | Apache-2.0 |
| 45 | microsoft/harrier-oss-v1-270m | 26% | 50% | 0.365 | 0.703 | 0.333 | MIT |
| 46 | ai-forever/ru-en-RoSBERTa | 22% | 46% | 0.325 | 0.690 | 0.331 | MIT |
| 47 | deepvk/USER2-small | 18% | 40% | 0.275 | 0.647 | 0.412 | Apache-2.0 |
| 48 | sentence-transformers/static-similarity-mrl-multilingual-v1 | 14% | 34% | 0.229 | 0.443 | 0.367 | Apache-2.0 |
| 49 | bm25 (Ollama) | 17% | 30% | 0.225 | — | — | — |
| 50 | paraphrase-multilingual (Ollama) | 14% | 33% | 0.218 | 0.415 | 0.312 | Apache-2.0 |
| 51 | jinaai/jina-embeddings-v2-base-code | 8% | 21% | 0.140 | 0.657 | 0.370 | Apache-2.0 |
| 52 | nomic-ai/CodeRankEmbed | 5% | 13% | 0.089 | 0.729 | 0.399 | MIT |
| 53 | bge-large (Ollama) | 4% | 8% | 0.057 | 0.604 | 0.318 | MIT |
| 54 | snowflake-arctic-embed:335m (Ollama) | 3% | 7% | 0.049 | 0.534 | 0.320 | Apache-2.0 |
| 55 | mxbai-embed-large (Ollama) | 3% | 7% | 0.048 | 0.537 | 0.295 | Apache-2.0 |
| 56 | granite-embedding:30m (Ollama) | 2% | 6% | 0.040 | 0.609 | 0.376 | Apache-2.0 |
| 57 | snowflake-arctic-embed:137m (Ollama) | 2% | 6% | 0.040 | 0.462 | 0.253 | Apache-2.0 |
| 58 | all-minilm:33m (Ollama) | 2% | 4% | 0.030 | 0.396 | 0.233 | Apache-2.0 |
| 59 | snowflake-arctic-embed:110m (Ollama) | 2% | 4% | 0.025 | 0.438 | 0.229 | Apache-2.0 |
| 60 | snowflake-arctic-embed:33m (Ollama) | 2% | 4% | 0.025 | 0.344 | 0.194 | Apache-2.0 |
| 61 | all-minilm:22m (Ollama) | 1% | 4% | 0.020 | 0.240 | 0.168 | Apache-2.0 |
| 62 | nomic-embed-text:v1.5 (Ollama) | 1% | 3% | 0.018 | 0.342 | 0.175 | Apache-2.0 |
| 63 | snowflake-arctic-embed:22m (Ollama) | 1% | 2% | 0.015 | 0.231 | 0.163 | Apache-2.0 |

Giga-Embeddings-instruct-3B и Giga-Embeddings-instruct-10B статистически неотличимы друг от друга, все остальные
модели отстают от них значимо. Модели с пометкой Ollama запускались через Ollama, остальные через
sentence-transformers.

На вопросах «где используется» все модели слабые, потому что правильных ответов там несколько и они похожи
друг на друга только именем. Тут помогает не другая модель, а гибридный поиск: если смешать векторную выдачу с
полнотекстовой (BM25), MRR@10 поднимается до 0.61–0.65 у всех проверенных моделей.

## В чём именно какая модель лучше

Обычные вопросы мы разделили по смыслу и по тому, какой код за ними стоит, и посмотрели, кто лидирует в каждой
группе. Значения в скобках это MRR@10.

| Группа вопросов | 1-е место | 2-е место |
|---|---|---|
| Как работает какой-то код | Giga-3B (0.868) | Giga-10B (0.865) |
| Что происходит при определённом условии | Giga-3B (0.801) | Giga-10B (0.779) |
| Какие есть поля и параметры | Giga-10B (0.863) | Giga-3B (0.855) |
| Где это реализовано | Giga-10B (0.887) | Giga-3B (0.872) |
| Зачем сделано именно так | Giga-3B (0.868) | pplx-embed-v2-late-0.6b (0.855) |
| В вопросе назван класс или метод | Giga-3B (0.880) | Giga-10B (0.869) |
| Где используется класс или метод | bge-code-v1 (0.503) | Qwen3-Embedding-4B q4 (0.450) |
| В нужном коде только английские комментарии | Giga-3B (0.843) | Giga-10B (0.816) |
| В нужном коде есть русские комментарии | Giga-3B (0.852) | Giga-10B (0.850) |
| В проекте есть почти копия нужного кода | F2LLM-v2-4B (0.805) | Giga-3B (0.788) |

Остальные места и все модели по каждой группе есть в [подробном отчёте](results/report.md).

## Как мерили

Взяли пять открытых проектов, по одному на язык: [SyTester](https://gitverse.ru/sbertech/sytester) на Java,
[giga_agent](https://gitverse.ru/GigaTeam/giga_agent) на Python, [onebase](https://github.com/ivanarama/onebase)
на Go, [OneScript](https://github.com/EvilBeaver/OneScript) на C# и [ui-kit-ce](https://gitverse.ru/sbertech/ui-kit-ce)
на TypeScript. Точные версии (коммиты) указаны в [методике](METHODOLOGY.md).

Каждый файл порезали на куски по синтаксису языка, так что один кусок это один класс, метод или функция. Если
кусок длиннее 2000 символов, его режем дальше на окна по 1500 символов, соседние окна перекрываются на 300
символов. В начало каждого окна дописана строка с главным именем куска, файлом и слоем, например
`// Context: RollupOptions | // Location: rollup.go (Layer: OTHER)`. Модель превращает в вектор каждое окно, а при подсчёте кусок
получает оценку своего лучшего окна. Всего получилось от 3600 до 5900 окон на проект.

К этим кускам составлено 2454 вопроса: 2000 обычных, где нельзя называть классы и методы, 204 с именами и 250
вопросов «где используется». Спорные ответы перепроверил Claude: в 1038 вопросах он вслепую оценил, какие из
найденных кусков на самом деле отвечают. Исходная разметка подтвердилась в 98% случаев, и места лидеров от
этого не поменялись.

Подробности о методике и о формате вопросов лежат в [METHODOLOGY.md](METHODOLOGY.md), сами вопросы в папке
[data](data), полная таблица всех моделей в [results/leaderboard.csv](results/leaderboard.csv).
