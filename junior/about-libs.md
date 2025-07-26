# Think twice when you ready to add new library in project

*You don’t need most of them*

This article about mobile dev lib, but reasons fit for Front end and Back end

People really likes to use libraries. hey helps you to get focus on other code aspects, they solves tasks for you and saves huge amount of time and money. They are tested by other people already, so they for sure works perfectly and 100% will help you.

Well, some people really think so, and they partly correct. In the past I loved to find new cool libraries that made my life easier and helped to concentrate on fast project evolving.

## Navigation 
- [Home](../)
- [Back](./)

## Content

1. [Why bundle your code and assets?](#notneed)
1. [Keep it simple stupid](#kiss)
1. [Don’t repeat yourself](#dry)
1. [Afterwords](#afterwords)
1. [Links](#links)


## <a name="notneed"></a>You aren’t gonna need it

### Libraries are made not for you

Well, they made of course for developers. But not for you concrete developer, not for your project. Library just helps to solve some task. More broad task more flexible and broad solution should be to cover most potential users (developers who will use this library)

### Libraries contain more functionality you actually need

This is consequence of previous point. When you try to make library, even smallest one and specific one (as I did for analytics, check out both articles here and here) , you started to think “What if a programmer will need this or that?”. After that of course you will ask yourself “You sure? Why would he need that?”. For some cases you find that actually bit of flexibility here and bit of flexibility there is important, although you personally don’t need it. Neither other user don’t need some of features, you use.

### Libraries don’t know your wishes

Previously I wrote about problem with Retrofit 2 and client-side caching mechanism. You can check it here. I wanted to make a unified cache mechanism for getting requests and responses which were organized through Retrofit (and I could not use appropriate headers since there was no support of them from server). And it became not so easy task. Eventually I wrote a workaround for that. But it is workaround, not actual solution. Because libraries are not sharpened for only you. Do not think that I blame Retrofit. No. It’s a really great library with exact aim (and my wish was just a superstructure only for me) and good code base and evolution cycle. What I want to say is libraries are not akinators or dogs. They can not predict your future wishes and they can not dynamically change only for you.

### Libraries consume your time
Previous items leads us here. When library have many aspects and settings to adjust it for developer’s aims, you need to spend time to investigate all features and possibilities of that library. More complex and flexible library becomes, more time you need to explore it. An interesting but today dead example of such library is Universal Image Loader. Moreover some libraries could be overloaded with solution variations for some task. This leads you to spending time to choose more appropriate solution for you. Such variations could appear because of different reasons. For example, legacy code. Dagger 2 is example for such library (check this). It great, but it really absorb all your free time in attempts to understand every single annotation.

### Libraries are unfriendly to your code.

Library does not know how you organize your code. How you designed dependencies injection. Do you use aforementioned Dagger? Do you use service locator? Do you gather all dependencies in application class? Or do you use other ways. To some extent it is good. We don’t want to have high coupling in the system. But we must be sanity. We can decouple every bit of functionality but this will lead to increasing complexity of the system. And every such increase must be justified.

### Libraries are unfriendly to each other

Same as a previous item, when you want to use multiple libraries across you code base, sometimes it leads to tiny specificities that you need to understand and resolve. Sometimes it can be really hard and requires either deep understand those libraries from your side or someone who stumbled on these specifities and wrote solution about that. It is not always easy to make Jackson, Dagger 2 and Lombok really good friends. Trust me. You will need to sacrifice libraries functinality for such collaborations. And voila, you can not use your favorite library for 100%. It isn’t critical, but harmful and sometimes painful.

### Libraries have their own evolution

You can pick a library today, but tomorrow it will be partly or completely different. And you may not like those changes. Yes, You may not migrating to new version, but suppose new version will optimize time or memory, fix critical bugs, that were reproduced by your production code, of course :) You can write an issue and hope that authors will agree with arguments you’ve provided. You use this library and adapt your code for new versions and spend time for it, but suddenly you see, that other library (couple of years ago pretty same as this) became more more rich and feature full. You could not predict that in the past. And now you need to choose. Are you ready to migrate to other library for cool features or not. Like migrating from Picasso to Glide. Or even worse, you’ve used library for year, studied it, researched its source code and then author wrote “sorry, no support any more”. Like it was in Universal Image Loader, Sherlock Action bar. Still as I said some of problems partly can be solved with proper decoupling. But this will cut some extra abilities of library and increase complexity of code base.

### Libraries have their own diseases

Every program has bugs. If program doesn’t have one it is probably useless. Every useful library contains bugs. Some of them are fixed fast, some kept inside from release to release becoming a chronic disease. Some of these disease are well known, other invisible for 99% users (except you, of course). Some diseases are not diseases at all for developers of library. Every library has that, you just need to admit and live with it.

All those aspects are eliminated, when you write your own solution. This solution will be for you and your team. It will contain exact functionality you need. It will be adjusted to your requirements, to your code base. And whats more important it will be fully controlled by you and thus will have exact evolution you need. It will be your responsibility to fix its bugs and optimize it, not just praying for “new version, that will fix everything”.

## <a name="kiss"></a> Keep it simple stupid

All this good in ideal world full of great and wise programmers with genius minds, but we live in real world. World of communication and interactions. World of continuous searching of best and simplest solution for known problems. In this world, we can not for 100% refuse libraries:

### Libraries still economize your time sometimes

Really discussible item if I remain it without explanation. As we understood earlier, libraries erase your time when you try to fix their diseases, you didn’t know earlier. They absorb your time, when you try to adjust then to other libraries and cram them all into the system you write. You will spend time on searching, researching and choosing competing library. But. In some cases, at some point library will save your time. If you want to draw graph, but you don’t know how to make custom views and support gestures on them, then MPAndroidChart can be helpful to you at start. Then you probably will realize, that there are huge amount of settings and the process of measure and layout is pretty slow. Moreover you can not use it with AsyncLayoutInflater and thus you can not use it with AsyncViewStub (i wrote it here, please, check).

### Libraries are mature

Some of them are grand-mature. Business guys just wanted to draw a pie chart and that’s all. But you used library, because you know…God told you…that you will need to use all those features in future. The truth is that imagined future probably (with very very high probability) will never come. Tomorrow They will come and ask you something that library will not be able to do, like animated changes in pie chart, and you will spread your hands and tell “that library is not able to do that, sorry” and give a proof. Really funny, as for me :)

### Libraries give you needed experience

And this only if you read source code. And understand that you use some library only to gather experience from its creators. It is a really good reason in such case, because library as other open source solution are the books of problem solutions. Unfortunately not everyone reads code. They just believe to the library and just use it.

### Libraries standardize solution and thus increase efficiency

Indeed! You use Guice in project and you hope that this is standard for all. Then you come to another project and find out, that they use Dagger 2. Okay, fair enough. This is your new standard right now. Tomorrow you will came to third project and observe next picture:

Kotlin ➡ Kodein (or Koin) ➡ New standard for you.

Other option when you start new project and you need to figure out will you use Picasso, Glide or Fresco. Each one have its own API with their own problems. And each choice will be different for different developers. Okay, but architecture will not change. Partly true. Yesterday you declare that MVP is best solution, and today androids without any doubt recommends MVVM for you with its brand new libraries (Jetpack). Today you think your standard is MVVM and tomorrow will come UDF. Today you using Java and thinking of migrating to Scala and tomorrow Android declare support for Kotlin. Standards are local both for projects and time.

There are standards like Code Smells, like SOLID, like Design Patterns. But even them are imply variations.

And last thing: think do you really need a full standardization? There are plenty of projects with their own requirements and possible features. There are different people with different taste and efficiency in different approaches to solving tasks. I would rather say yes to local standardization in terms of project/organization than to global standardization.

## <a name="dry"></a> Don’t repeat yourself

### You don’t need to reinvent the wheel

Someone will say “Why do I need to reinvent the wheel? There is a library and I just use it”. And I will say, that there are many misleads in life. For example, DRY principle. I was mistaken, too, at some time thinking that DRY is about absolute elimination of code duplications, but it appeared then, that this principle about little bit different thing.

Same applies here. I’ve heard many times that if you will not use library, but will write your own solution, you will reinvent the wheel. If you see library, investigate it and decide to put in your project the idea of that library adapted to your needs, it is not reinventing the wheel. “The bicycle” was already invented. You just took some spare parts and handle them to your future catamaran.

I want to stop right here and tell that the Idea is not to fully refuse all libraries. Libraries are great thing, but you just don’t need most of them. Only the small part.

### Make a wise choice
There are different characteristics of libraries:

- **Size.** Too big libraries can take your time to understand every corner, may contain more possible bugs and diseases and probably will be used not in a 100%, so their choice must be really justified. On a contrary small library, that contains only 1–5 classes, probably not so needed to be built in in project as dependency. In many times it is easier to understand it and add its code to your project adapted for your specific needs. There are libraries like LikeButton, which are very small and not so flexible. It will be better to adapt code for your needs including it in your project.
- **Aim.** Remember SRP from SOLID? I think in most cases library should exist only for one purpose. Otherwise it can be pretty messy. Personally I don’t really like libraries like Guava and KTX. They contains interesting util functions, but often you need only tiny part of them. For me much simpler just to include those functions in project utils. Especially if they small.
- **Popularity.** Less popular library becomes, less possibility that it will be supported in a long term, less possibility that it is more stable (count of issues and resolved issues) than popular analogues. There are exceptions, I’m sure. Just ask yourself, if you doing big project with great future, do you want really risk and put “small star count” library in your project?
- **Maintainability.** When library is not supported any more, or it took months to see new commit, it is not such a good value for adding such library into the project. Good libraries are constantly evolving.

I suppose to look up primary on not tiny and not monstrous libraries with exact aim, which are popular and maintained constantly. As for me RxJava is a good example. Yes, its really big, but it maintained every time. Retrofit, Dagger, Glide are good examples. Google Maps is good library, but it’s a little bit cheat, because this is complex integration library to make your app look more integrated in Android system. Every library, that provides sort of integration with big famous service is a good example.

You should pick up every library wisely and characteristics above can help you. But always remember that it is just an indication, not a requirement.

## <a name="afterwords"></a> Afterwords
I hope I didn’t harm anyone or wasted your time. My article was not about how terrible libraries are and we must avoid any of them. Still my post was sort of provocation. Provocation to think “Do you really need that library?” or “that one?”. There always should be sanity borders and my article was rather about situations when project has a lot of libraries, even “library zoo”.

Libraries are very good helpers, but we must always keep our minds clean and rational to put only strongly needed libraries in project. Not just anything because we too lazy or because of some hype framework.

So if you’ve finished that article and think “I already know all of that”, then great! Really! Because I faced with opposite situations.

## <a name="links"></a> Links
1. [medium](https://programmerr47.medium.com/think-twice-when-you-ready-to-add-new-library-in-project-70bc3bb87515)

## Navigation 
- [Home](../)
- [Back](./)