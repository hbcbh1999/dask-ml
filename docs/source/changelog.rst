Changelog
=========

Version 0.4.1
~~~~~~~~~~~~~

This release added several new estimators.

Enhancements
------------

Added :class:`dask_ml.preprocessing.RobustScaler`
"""""""""""""""""""""""""""""""""""""""""""""""""

Scale features using statistics that are robust to outliers. This mirrors
:class:`sklearn.preprocessing.RobustScalar` (:issue:`62`).

Added :class:`dask_ml.preprocessing.OrdinalEncoder`
"""""""""""""""""""""""""""""""""""""""""""""""""""

Encodes categorical features as ordinal, in one ordered feature (:issue:`119`).

Added :class:`dask_ml.wrappers.ParallelPostFit`
"""""""""""""""""""""""""""""""""""""""""""""""

A meta-estimator for fitting with any scikit-learn estimator, but post-processing
(``predict``, ``transform``, etc.) in parallel on dask arrays.
See :ref:`parallel-meta-estimators` for more (:issue:`132`).

Version 0.4.0
~~~~~~~~~~~~~

API Changes
-----------

- Changed the arguments of the dask-glm based estimators in
  ``dask_glm.linear_model`` to match scikit-learn's API (:issue:`94`).

  * To specify ``lambuh`` use ``C = 1.0 / lambduh`` (the default of 1.0 is
    unchanged)
  * The ``rho``, ``over_relax``, ``abstol`` and ``reltol`` arguments have been
    removed. Provide them in ``solver_kwargs`` instead.

  This affects the ``LinearRegression``, ``LogisticRegression`` and
  ``PoissonRegression`` estimators.

Enhancements
------------

- Accept ``dask.dataframe`` for dask-glm based estimators (:issue:`84`).

Version 0.3.2
~~~~~~~~~~~~~

Enhancements
------------

- Added :meth:`dask_ml.preprocessing.TruncatedSVD` and
  :meth:`dask_ml.preprocessing.PCA` (:issue:`78`)

Version 0.3.0
~~~~~~~~~~~~~

Enhancements
------------

- Added :meth:`KMeans.predict` (:issue:`83`)

API Changes
-----------

- Changed the fitted attributes on ``MinMaxScaler`` and ``StandardScaler`` to be
  concrete NumPy or pandas objects, rather than persisted dask objects
  (:issue:`75`).
