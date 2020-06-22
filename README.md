# Frozen_Dessert_Production-Forecasting
Forecasting Frozen Dessert Production using Recurrent Neural Network(RNN)

1) Data:

Info about this data set: https://fred.stlouisfed.org/series/IPN31152N


Units:  Index 2012=100, Not Seasonally Adjusted

Frequency:  Monthly

The industrial production (IP) index measures the real output of all relevant establishments located in the United States, regardless of their ownership, but not those located in U.S. territories.

NAICS = 31152

Source Code: IP.N31152.N

Suggested Citation:
Board of Governors of the Federal Reserve System (US), Industrial Production: Nondurable Goods: Ice cream and frozen dessert [IPN31152N], retrieved from FRED, Federal Reserve Bank of St. Louis; https://fred.stlouisfed.org/series/IPN31152N, November 16, 2019.


2) Train/Test split

3) Scaling


4) TimeSeriesGenerator for scaled_train data:


        from tensorflow.keras.preprocessing.sequence import TimeSeriesGenerator
        
        length = 18
        
        n_features = 1
        
        generator = TimeSeriesGenerator(scaled_train, scaled_train, length=length, batch_size=1)
        
        
5) Create the model:


        from tf.keras.models import Sequential
        
        from tf.keras.layers import Dense, LSTM
        
        
        model = Sequential()
        
        model.add(LSTM(100, activation='relu', input_shape=(length, n_features)))
        
        model.add(Dense(1))
        
        model.compile(optimizer='adam', loss='mse')
        
        
        model.summary()
        
        
6) TimeSeriesGenerator for scaled_test data:


        validation_generator = TimeseriesGenerator(scaled_test, scaled_test, length=length, batch_size=1)


7) Early_stop:


        from tf.keras.callbacks import EarlyStopping
        
        early_stop = EarlyStooping(monitor='val_loss', patience=2)
        
        
8) Fit the model:


        model.fit_generator(generator, validation_data=validation_generator, epochs=20, callbacks=[early_Stop])
        
        
9) Evaluation

10) Forecasting into the unknown Future











