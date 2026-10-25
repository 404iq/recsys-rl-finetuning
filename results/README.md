# results

Лёгкие результаты полного прогона `solution.ipynb` на Kaggle. Суффикс `full` – полный прогон, `s250_lr3e-05` – настройки RL (250 шагов, lr 3e-5). Тяжёлые артефакты (чекпойнты, кэш рекомендаций) в репозиторий не входят.

| Файл | Что внутри |
|---|---|
| `split_stats_full.json` | размеры train/val/test, число eval-пользователей, доля объектов вне словаря |
| `base_train_log_full.csv` | обучение GPT-2 по эпохам: loss и Recall@10 на val |
| `base_val_full.json` | бейзлайны и GPT-2 на val: метрики с 95% ДИ |
| `rm_train_log_full.csv`, `rm_val_full.json`, `rm_test_full.json` | reward model RM-A: обучение, качество на val и test против бейзлайнов |
| `rm_calibration_full.csv` | калибровка RM-A по децилям предсказания (val) |
| `rm_b_train_log_full.csv` | обучение RM-B (независимая проверка) |
| `rm_ret_train_log_full.csv`, `rm_ret_val_full.json` | RM-ret (возврат за 3 дня): обучение и AUC на val |
| `rl_base_*.json`, `rl_<прогон>_*.json` | итог каждого RL-прогона на val: релевантность, reward по трём RM, поведение |
| `rl_log_<прогон>_*.csv` | траектория обучения RL: reward, KL, энтропия, Recall@10 и reward на подвыборке val |
| `rl_delta_*.json` | разности с базой: Recall@10, NDCG@10, reward, парный бутстреп |
| `rl_observed_*.csv` | фактический досмотр и возврат рекомендованных объектов по данным val |
| `rl_set_relevance_*.csv` | релевантность по 6 следующим событиям |
| `rl_familiarity_*.csv` | жанровое сходство рекомендаций с историей пользователя |
| `rl_gain_confirmed_*.csv` | какая часть прироста reward подтверждается фактом |
| `rl_seeds_*.csv` | разброс между запусками с разным seed |
| `multistep_*.json` | генерация на 5 шагов: режимы free и teacher |
| `test_*.json` | финальная оценка на test: база, бейзлайны, RL-прогоны |
| `fig_pareto_*.png`, `fig_tradeoff_*.png`, `fig_multistep_*.png`, `fig_test_*.png` | рисунки из ноутбука |

Имена прогонов: `pct_b<β>` – награда «доля просмотра» с коэффициентом KL β; `pct+hit` – с бонусом за совпадение с реальным следующим объектом; `pct+div`, `pct+div_hi` – со штрафом за скопление; `long`, `long_b0.1` – возврат за 3 дня; `pct+long` – смесь; `pct_H5` – горизонт 5 шагов; `pct_b0.1_ent*` – с бонусом за энтропию; `*_s1`, `*_s2` – повторы с другим seed.
