.. -*- mode: rst -*-

ROCAUC
======

A ROCAUC (Receiver Operating Characteristic/Area Under the Curve) plot allows the user to visualize the tradeoff between the classifier's
sensitivity and specificity.

.. code:: python

    from sklearn.model_selection import train_test_split

    # Load the classification data set
    data = load_data("occupancy")

    # Specify the features of interest and the classes of the target
    features = ["temperature", "relative humidity", "light", "C02", "humidity"]
    classes = ["unoccupied", "occupied"]

    # Extract the numpy arrays from the data frame
    X = data[features].as_matrix()
    y = data.occupancy.as_matrix()

    # Create the train and test data
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

.. code:: python

    from sklearn.linear_model import LogisticRegression

    from yellowbrick.classifier import ROCAUC 

    # Instantiate the classification model and visualizer
    logistic = LogisticRegression()
    visualizer = ROCAUC(logistic)

    visualizer.fit(X_train, y_train)  # Fit the training data to the visualizer
    visualizer.score(X_test, y_test)  # Evaluate the model on the test data
    g = visualizer.poof()             # Draw/show/poof the data



.. image:: images/rocauc.png


API Reference
-------------

.. automodule:: yellowbrick.classifier.rocauc
    :members: ROCAUC
    :undoc-members:
    :show-inheritance:
