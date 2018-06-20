# Network and Types - the Future of Akka

* Actors
  * "valid complaints" complaints with classic actors
    * can send wrong message
    * interop with futures/mutable "sender()" / accidental closing over m. state
    * actors don't compose! (the same as functional concepts do)
  * Akka team extras
    * flow -control not built into Actor messaging
    * supervison - too often misunderstood/abused/backoff limitations
    * actorSelection - feature aboused (String => ActorRef)

* These weren't goals of actors
  * not entirely pure
  * Super mega high performance
  * build only for the local case

* Untyped (Classic) Actors
  * "sender()" propagated automatically
  * any message

* Akka Actor Typed
  * sender is part of the protocol
   * Only the right type of message can eb sent
   * behaviors always return 

* Actors & Types = Akka Actor Typed
  * cutting off the name eventual because it will be the main thing
  * It is really all about ActorRef[T] 
    * solves complaint 1 and the hard to navigate code
    * It is not the main change - compositional power of Behavior[T] which can properly functial compose

* ActorSystem is an Actor
* Spwaning requires a name unless you use spawnAnonymous
* Behavior recieve 
  * multiple imlementations with different sort of typed information you might want to use (cut down on what you are recieving)
* All behavior changes returns Behaviors
* can co-exist with untyped actors
  * currently running on an emulation layer of untyped actors
  * used to help migrating existing code

* Behavior[T] solves biggest complaint 
  * setup - replaces pre-start and you get the context
  * resuing - compose through partial functions 
    * state as a parameter (no var)
  * union types (which don't exist) could be really useful
    * wait till Scala 3 and will fit the model

  * Type narrowing can be used to get the right actor ref
  * Use widen to widen the set of messages by adapting them or leaving them unhandled
    * partial function so anything unhandled becomes unhandled
  * Another approach which is the "right way" is to have a message adapter
    * context.messageAdapter - to transform the message to what you handle
  * Or the ask pattern - this is more verbose and fairly complex with lots of versions of the method

* How can ActorRef[T] recieve lifecycle messages
  * can't just recieve type T because that's typed message
  * difference between message and signals
  * signals get their own recieve block
  * somewhat workaround because of lack of unit type
  * works well because you only care about the signals you care about

* Deprecation of actorSelection - Abuse of [system|context].actor system
  * dead letters - sending messages to dead actors (different from unhandled)
  * Use strings to create names to look up actors
    * could reference actors that don't exist
    * can't express this typed actors
  * Replace with receptionist
    * are they there? If no wait to see they show up (or can timeout)
    * just a normal actor that handles Recptionist.Command
    * actors register with the ServiceKey
* Mutable Behavior[T]
  * intended to have mutable state in the fields - this is a 1:1 mapping with classic Actors

* Changes in supervistion
  * If you want supervision you have to apply it
  * if you wanted it you wanted you had to implement in parent actor
  * It was often abused
  * Now you just wrap the behavior with the supervision strategy
    * making it more composable
    * in wrapping it just comes along with the behavior

    