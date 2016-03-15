# Map app

## Hantering av gester och Map Kit i Swift

Både iPhone och iPad är i grund och botten (multi)touch-enheter. Detta innebär så klart att inmatning till enheterna görs med hjälp av olika fingergester, antingen med en eller flera fingrar. I iOS är det väldigt lätt att hantera gester med hjälp av så kallade gesture recognizers. Det finns färdiga recognizers för de flesta standardmässiga gester, såsom "tap", "swipe" och "pinch". Det går också att utöka med egna subklasser som hanterar andra gester. Detta gör att man med bara några få rader kan hantera till exempel en swipe-rörelse över skärmen utan krångel.

En väldigt vanlig kategori av appar på App Store är sådana som hjälper användaren att hitta diverse geografiska platser. Apple har gjort det enkelt för oss att skapa sådana appar genom att tillhandahålla en färdig vy som sköter interaktion med och nedladdning av kartdata. Denna vy är del i ramverket Map Kit som ni kommer att få testa på i denna uppgift. Ni kommer dessutom lära er hur man kan använda gesture recognizers för att lägga till ytterligare interaktion till existerande vyer, så som till exempel en karta.

Swift är Apple's nya programmerings språk som skiljer sig en del från Objective-C. Swift är ett definierat som ett protokoll orienterat språk. Det betyder att det är den paradigmen som är förespråkat att använda när man skriver sin kod. Men det går fortfarande bra att skriva objekt orienterad kod i Swift för den som inte hunnit lära sig den nya paradigmen än. Denna laboration kommer inte kräva att du demonsterar full kunskap av Swift utan är mer tänkt så du får testa språket.

# Förberedelser

#### Länkar

* Guider 
	* [Location and Maps Programming Guide - Displaying Maps][displaying-maps]
	* [Location and Maps Programming Guide - Getting the User’s Location][getting-the-users-location]
	* [Location and Maps Programming Guide - Annotating Maps][annotating-maps]
	* [Event Handling Guide for iOS - Gesture Recognizers][gesture-recognizers]
	* [The Swift Programming Language][swift-programming-language]
* Dokumentation
	* [MKPointAnnotation][point-annotation]
	* [MKMapView][map-view]
	* [MKUserTrackingBarButtonItem][user-tracking-bar-button-item]
	* [UIGestureRecognizer][gesture-recognizer]
	* [UITapGestureRecognizer][tap-gesture-recognizer]
* Screencasts
	* [MapKit][map-kit]
	* [Introduction to Swift][swift]


[displaying-maps]:https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/MapKit/MapKit.html#//apple_ref/doc/uid/TP40009497-CH3-SW1

[getting-the-users-location]:https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html#//apple_ref/doc/uid/TP40009497-CH2-SW1

[annotating-maps]:https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/AnnotatingMaps/AnnotatingMaps.html#//apple_ref/doc/uid/TP40009497-CH6-SW1

[gesture-recognizers]:https://developer.apple.com/library/ios/documentation/EventHandling/Conceptual/EventHandlingiPhoneOS/GestureRecognizer_basics/GestureRecognizer_basics.html

[point-annotation]:https://developer.apple.com/library/ios/documentation/MapKit/Reference/MKPointAnnotation_class/index.html#//apple_ref/occ/cl/MKPointAnnotation

[swift-programming-language]:https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/index.html

[map-view]:https://developer.apple.com/library/ios/documentation/MapKit/Reference/MKMapView_Class/index.html#//apple_ref/occ/cl/MKMapView

[user-tracking-bar-button-item]:https://developer.apple.com/library/ios/documentation/MapKit/Reference/MKUserTrackingBarButtonItemClassRef/index.html#//apple_ref/occ/cl/MKUserTrackingBarButtonItem

[gesture-recognizer]:https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIGestureRecognizer_Class/index.html#//apple_ref/swift/cl/c:objc(cs)UIGestureRecognizer

[tap-gesture-recognizer]:https://developer.apple.com/library/ios/documentation/UIKit/Reference/UITapGestureRecognizer_Class/index.html#//apple_ref/occ/cl/UITapGestureRecognizer

[map-kit]:http://www.ida.liu.se/~725G72/material/screencasts/mapkit.mp4

[swift]:http://www.ida.liu.se/~725G72/material/screencasts/swift.mp4

#### Frågor

Inga frågor är märkta för att redovisas till denna uppgift.

1. Den abstrakta basklassen som alla gest-klasser ärver från heter UIGestureRecognizer - vilka konkreta subklasser finns det? Vilken typ av gest motsvarar respektive klass?

2. Hur använder du UISwipeGestureRecognizer för att hantera en "swipe" rörelse från höger till vänster? Gör egna antagande om variabler och dess typer (förklara dock vad som är vad).

3. Om du inte skulle använda klassen ovan för att hantera swipe-rörelsen, hur skulle du då bära dig åt? Vilka metoder behöver du implementera? Du behöver inte skriva någon kod eller förklara i yttersta detalj, huvudsaken är att du visar att du förstår skillnaden mellan dessa metoder. Vilken av dessa två sätt att hantera gester (alltså att manuellt hantera gester, som du beskrivit här eller att använda UIGestureRecognizer-klasser) tycker du verkar enklast/bäst?

4. Med en MKMapView vill man ofta visa användarens position. Hur går man till väga för att göra det på ett enkelt och användarvänligt sätt?

5. För att lägga in kartnålar (annotations) i en kartvy behöver flera klasser samverka. Förklara hur det går till när en kartnål visas, vilka sorts klasser som behövs och vad de har för uppgift.

## Uppgift

I den här uppgiften ska du testa på att använda en kartvy, men även att hantera gester. Skapa ett nytt projekt i Xcode, utgå från en "Single View Application". Du får själv välja om du vill utveckla till iPhone eller iPad (båda behövs ej). Lägg till en MKMapView i den tomma vyn. Implementera nu stöd så att följande kan göras:

Användaren ska kunna växla karttyp på ett enkelt sätt (förslagsvis med en UISegmentedControl).
Man ska kunna sätta på positionering av användaren med hjälp av en MKUserTrackingBarButtonItem.
Användaren ska kunna toggla på/av ett läge för att lägga till kartnålar till kartan genom att trycka på kartan. Kartnålarna ska dyka upp på de koordinater där användaren trycker. Ett tips är att UIGestureRecognizers har en "enabled" property för att sätta på eller stänga av igenkänning av gesten.
För att få plats med kontroller som styr ovanstående funktioner är det lämpligt att kapsla in vy-kontrollern i en UINavigationController och använda utrymmet i dess navigation bar. Utgå gärna från exempelappen som gjordes i screencasten om Map Kit. Du måste dock sätta upp projektet själv - till denna laboration finns det inget färdigt kodskelett.

Denna uppgift ska göras i Swift. Det betyder att all kod som lämnas in ska vara skriven i Swift.

## Redovisning

Packa ihop projektet och skicka per mail till din handledare. Ange '725G72 - Laboration 5 - Redovisning' som ämne. Skriv med vad du har för LiU-id (t ex abcde123) om du inte mailar från din studentadress.
