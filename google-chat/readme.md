## Google Chat 

Send a message to a Google Chat space

[API Docs - Incoming Webhooks](https://developers.google.com/chat/how-tos/webhooks)

<img src="custom-template-google-chat-screenshot.png" alt="image_tooltip" width="500"/>

### Template 

- [body.liquid](body.liquid)

- HTTP Server URL: `https://chat.googleapis.com/v1/spaces/0000000000/messages?key=0000000000000000000000000000000000`

```body.liquid
{
    "cards": [
        {
            "header": {
                "title": "{{alertType}}",
                "subtitle": "{{organizationName}} - {{networkName}}"
            },
            "sections": [
                {
                    "widgets": [
                        {
                            "textParagraph": {
                                "text": "<b>Device Name:</b> {{deviceName}}<br><b>Device Serial:</b> {{deviceSerial}}<br><b>Device MAC:</b> {{deviceMac}}<br><b>Device Model:</b> {{deviceModel}}"
                            }
                        },
                        {
                            "textParagraph": {
                                "text": "<b>Alert ID:</b> {{alertId}}<br><b>Alert Level:</b> {{alertLevel}}<br><b>Occurred At:</b> {{occurredAt}}"
                            }
                        },
                        {
                            "textParagraph": {
                                "text": "<b>Alert Data:</b><br>{{alertData | json_markdown}}"
                            }
                        },
                        {
                            "buttons": [
                                {
                                    "textButton": {
                                        "text": "VIEW ORGANIZATION",
                                        "onClick": {
                                            "openLink": {
                                                "url": "{{organizationUrl}}"
                                            }
                                        }
                                    }
                                },
                                {
                                    "textButton": {
                                        "text": "VIEW NETWORK",
                                        "onClick": {
                                            "openLink": {
                                                "url": "{{networkUrl}}"
                                            }
                                        }
                                    }
                                },
                                {
                                    "textButton": {
                                        "text": "VIEW DEVICE",
                                        "onClick": {
                                            "openLink": {
                                                "url": "{{deviceUrl}}"
                                            }
                                        }
                                    }
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```