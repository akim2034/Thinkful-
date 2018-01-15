# Thinkful-

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

df = pd.read_csv('ted_main.csv')
df.columns

df = df[['name', 'title', 'description', 'main_speaker', 'speaker_occupation', 'num_speaker', 'duration', 'event', 'film_date', 'published_date', 'comments', 'tags', 'languages', 'ratings', 'related_talks', 'url', 'views']]

import datetime
df['film_date'] = df['film_date'].apply(lambda x: datetime.datetime.fromtimestamp( int(x)).strftime('%d-%m-%Y'))
df['published_date'] = df['published_date'].apply(lambda x: datetime.datetime.fromtimestamp( int(x)).strftime('%d-%m-%Y'))

df.head()

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.scatter(x=df['views'], y=df['duration'])
plt.title('Duration and Views')
plt.ylabel('Duration in seconds')
plt.xlabel('View Count')

plt.subplot(1, 2, 2)
plt.plot(df['views'], color='purple')
plt.title('Views')

plt.tight_layout()
plt.show()

plt.plot(df['comments'])
plt.title('Comments')

plt.show()

mean = np.mean(df['comments'])
median = np.median(df['comments'])

print("Mean is: " + str(mean))
print("Median is: " + str(median))

plt.boxplot(df['views'])
plt.tight_layout()
plt.show()
