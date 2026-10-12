# Optuna usage

Historical hyperparameter-tuning notes:

## 1. Install

```python
    pip install optuna
```

## 2. Import

```python
    import optuna
    from optuna import Trial
```

## 3. Choose a sampler

```python
    from optuna.samplers import TPESampler
```

See [samplers](https://optuna.readthedocs.io/en/stable/reference/samplers/index.html) for alternatives.

## 4. Define an objective

Use `trial.suggest_*` to specify parameter ranges and choices. Where applicable, supply the parameter name, lower/upper bounds and optional step, then train and evaluate the model inside the objective.

```python
        params = {
                'objective': 'binary',
                'bagging_fraction': trial.suggest_float("bagging_fraction", 0.5, 0.6, step=0.01),
                'bagging_seed': 11, ##
                'learning_rate': trial.suggest_categorical("lr", [0.001, 0.005, 0.01, 0.05, 0.1]),
                'num_iterations': trial.suggest_int("n_iter", 100, 1000, 100),
                'max_depth': trial.suggest_categorical('max_depth', [-1, 1]), # need to consider
                'boosting': 'gbdt',
                'early_stopping': trial.suggest_categorical('patience', [0, 5, 10, 15, 20])
            }
```

See [Trial API](https://optuna.readthedocs.io/en/stable/reference/generated/optuna.trial.Trial.html). The original example is retained; library signatures and model parameters may differ by version.

## 5. Optimize a study

```python
    sampler = TPESampler(seed=42)
    study = optuna.create_study(
        study_name="lgbm_parameter_opt",
        direction="maximize",
        sampler=sampler,
    )
    study.optimize(objective, n_trials=10)
    print("Best Score:", study.best_value)
    print("Best trial:", study.best_trial.params)
```

## 6. Example result

![image](https://user-images.githubusercontent.com/90206705/217500956-ce83e667-ce06-4179-92b4-8b2f4408108a.png)


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/optuna-%EC%82%AC%EC%9A%A9%EB%B2%95)
