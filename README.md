## opus123

opus123 - command-line Opus codec radio player (like ogg123 or mpg123).
Listen internet radio station + display meta tags for songs

## USAGE

    opus123 [url|-shotcut] [dev]

## EXAMPLES

    opus123 http://ai-radio.org
    opus123 http://ai-radio.org/128.opus default
    opus123 http://ai-radio.org/320.opus plughw:CARD=DragonFly,DEV=0
    opus123 -airadio
    opus123 -1
    AUDIODEV=plughw:CARD=HDMI,DEV=7 opus123
    opus123 --show-config

## DOWNLOAD & INSTALL

    wget https://raw.githubusercontent.com/hyphop/opus123/master/opus123
    chmod 0755 opus123 
    ./opus123 

or 

    git clone https://github.com/hyphop/opus123.git
    cd opus123.git
    ./opus123
    

## AUDIO OUTPUT backend
    
by default **audio_out** use aplay or sox, but u can use any via **audio_out** config variable 

EXAMPLE

use mpv and ladspa filter 

    audio_out="mpv \
    --really-quiet --quiet  --no-video  --audio-display=no \
    --demuxer=rawaudio \
    --demuxer-rawaudio-rate=48000 \
    --demuxer-lavf-probesize 65536 \
    --demuxer-lavf-buffersize 65536 \
    -ao=alsa:device=[$AUDIODEV] \
    --af=ladspa=${LADSPA_PATH}vynil_1905.so:vynil:[1981,66,0.3,0.3,0.2] \
    -"

use aplay - default alsa audio command-line player

    audio_out="aplay -q"

use paplay - pulse audio

    audio_out="paplay"

## CONFIG FILES

    /etc/opus123.conf  - system config
    ~/.opus123rc       - user config

example

    #audio_dev=alsa_pcm_name
    #audio_dev=default
    reconnect_auto=1
    stream_default=http://ai-radio.org/64.opus
    stream_1=http://ai-radio.org/128.opus
    stream_3=http://ai-radio.org/320.opus

## CONFIG VARS

    audio_out           - audio backend player
    audio_dev           - audio device name
    reconnect_auto      - reconnect if lost or broken network connection
    audio_filter        - audio pipe filter 
    stream_default      - default stream url
    stream_*            - another stream url


## NOTE

opus123 writed for [http://AI-Radio.org](http://AI-Radio.org) opus streams test! play all opus streams and display meta ok!
sure u can listen any other radio stream too;)

## LINKS

* [https://github.com/hyphop/opus123.git](https://github.com/hyphop/opus123.git)
* [http://ai-radio.org/chronos/2015-06-08-opus123-command-line-radio-player](http://ai-radio.org/chronos/2015-06-08-opus123-command-line-radio-player)
* [http://ai-radio.org/streams/](http://ai-radio.org/streams/)
* [http://dir.xiph.org/by_format/Opus](http://dir.xiph.org/by_format/Opus)

## AUTHOR 

    ## hyphop ##
