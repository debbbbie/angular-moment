## Customerize updateTime inverval

```
                        function updateTime(momentInstance) {
                            element.text(momentInstance.from(getNow(), withoutSuffix));

                            if (titleFormat && !element.attr('title')) {
                                element.attr('title', momentInstance.local().format(titleFormat));
                            }

                            if (!isBindOnce) {

                                var howOld = Math.abs(getNow().diff(momentInstance, 'minute'));
                                var secondsUntilUpdate = 3600;
                                // TODO from here
                                if (howOld < 1) {
                                    secondsUntilUpdate = 1;    
                                } else if (howOld < 60*24) { // within 24 hours, refresh per 30 seconds.
                                    secondsUntilUpdate = 30;
                                //} else if (howOld < 180) {
                                //    secondsUntilUpdate = 300;
                                }
                                // end of TODO from here

                                activeTimeout = $window.setTimeout(function() {
                                    updateTime(momentInstance);
                                }, secondsUntilUpdate * 1000);
                            }
                        }
```                        
