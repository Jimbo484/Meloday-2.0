# Meloday-2.0
Updated version of the great intelligent Plex playlist creator by trackstarter, featuring new options like ratings and playlist selector.

HOW TO INSTALL:

1. Install python. Here is the downloads page: https://www.python.org/downloads/ Scroll down and find the relevant version. Install it, I know python can be scary for some, but not too much technical brain is required for this installation.

2. Download my new version of Meloday here on github. Put this folder wherever you want. Now wherever you put the folder, while in file explorer right click near the top of the tab where it shows the location (Mine is in downloads, so it shows Downloads > Meloday) and copy address as text. Now open a cmd prompt (I press windows key + r to open run, then type cmd, but you can also just search command prompt in windows). In the command prompt window, type cd (the location you copied). So mine is cd C:\Users\my name\Downloads\Meloday (don't forget the cd at the start). Now type or copy the following: pip install -r requirements.txt in command prompt. This will install some necessities in order for this thing to work.
 
3. In the folder, you will see a config.yml file. Edit it with notepad to configure the file. This is where you can customize your experience.
On the top inside config.yml, you will need 3 things: Your plex url, your plex token, and the name of your music library. I know you might be thinking "damn, this is too much work..." But it isn't as hard as it may seem.

-To get your plex url, right click your plex media server tray icon on the bottom right of your taskbar and click open plex. This should open an internet tab for Plex. What you need is in the search bar. It should say something like http://IPADDRESS:32400/web/index.html#!/. What you need is this: http://IPADDRESS:32400. Copy that and paste it in the "" url section of the config.yml file. 

-To get the token, using the same method to get the url, log in to your plex account. Hit the music notes on the left side of the screen and click the first album that pops up on your screen. You want to see the tracks. On the right side of the tracks, there will be 3 vertical dots. Click Get Info near the bottom, and if you scroll down a bit on the page, you should see a view XML file. Click that, which will open up a white page with a bunch of blue and red letters and numbers. Now on that page, click and hold the search bar and drag it all the way to the right, and in there it will say Plex-Token=YOUR PLEX TOKEN (Should be a bunch of random numbers and letters. Copy that value and paste it into the Token section of the config.yml file. 

-The last thing is the name of your music library. Mine is music, yours might be different. This isn't the desktop name, just the music library name as it appears on Plex.

5. Edit whatever else you want in the config file. There reference tracks and sonically similar tracks. It doesn't use AI, it only uses sonic metadata, so I don't think this will work if you don't have premium. Reference tracks are ones that Meloday tries to find sonic similarity based on. Keep in mind there is a default artist_ratio of max tracks * .05 and a genre_ratio of max tracks * .1. This means the maximum number of same genres and same artists can only be that much in the playlist. I can add an option for the future to alter this. The flow of options goes like this:

-source_playlist (NEW! If not blank, only considers reference tracks from playlist.)

-use_time_periods (NEW! If 1, will perform as before, considering the time period in which you listened to add reference tracks to the pool. If 0, it will consider all tracks.)

-exclude_played_days (Ignore tracks played withing the last X days when considering reference tracks.)

-history_lookback_days (Only considers reference tracks played within the last X days)

-Max Tracks (Max amount of tracks in playlist)

-Min ratings (NEW! Only considers tracks with this rating or higher for reference tracks, albums or artists. The way Plex's rating system works is 0-10, or 1-5 stars including half. 0 will consider all tracks up to this point and any other number considers the star ratings of tracks. 10 = 5 stars, 7 = 3.5 stars, etc. So each half star is 1.  Can do artist, album or track.)

-historical_ratio (This is the percentage of reference tracks that are going to actually be in your playlist. This = max tracks * historical ratio. So if I had 50 tracks, there will be around 16 (sometimes more, sometimes less) reference tracks in the playlist. These are the tracks the sonic data take from.)

-sonic_similar_limit (Number of sonically similar tracks to fetch from reference tracks. This considers the most sonically similar to the least sonically similar. So If I have 16 reference tracks, it will pull 20 tracks from each of those (only if there are that many sonically similar tracks for each of the songs, if that was so, We'd technically have 320 sonically similar tracks)).

-sonic_similarity_limit (This has to do with playlist flow, and this option should not be higher than max tracks. This will consider the songs from the sonic_similar_limit (in our example, 320 songs) and put them in a smooth order. It will take a track, take this amount of tracks in our pool, and find the closest in similarity. Then from that song, it will pick this amount more and find the most sonically similar, and so on and so fourth.) 

-sonic_similarity_distance. (This considers how sonically similar each track has to be from the reference track. This can be 0. The smaller, the more similar the sonically similar song has to be to the reference track to get picked. In my experience, 0 = 95%+ sonically similar, 0.1 = 85%+ or so, 0.2 = 75%+ or so)

6. Double click meloday.py and it should pop up a cmd prompt screen showing the progress of the playlist creation. Once it is done, it should pop up in your playlist list. It will consider the time of the playlist creation even if use_time_periods is 0, but it will work.

6. Enjoy!
