# ASYNCIO library
This toolkit is Python's answer to writing clean, efficient, and scalable code for concurrent I/O operations.

AsyncIO is perfect when you have many parallell I/O operations (I/O bound programs).
The library allows you to do multiple things at once, without doing them at the same time.

It does not run in multiple threads, but it allows multiple functions to run concurrently in a simple thread.

## Example tasks
- Fetching multiple web pages in parallell, using *aiohttp* library
- Reading files in parallell, using *aiofiles* library

## Core concepts
- **Event Loop**: The central scheduler of asyncio, it is responsible for event handling and routine scheduling.
- **Coroutines**: Python functions declared with `async def`. These functions can be paused and resumed at `await` points.
- **Futures**: Objects that represent the result of some work that has not yet completed.
- **Tasks**: Scheduled coroutines that are wrapped into a Future object.

## Keywords

### await
 - The `await` keyword is essential, as it allows the scheduler to pause the execution of an async function until an 
awaitable object has completed.
 - The keyword can only be used inside an *async* function, a coroutine, and in front of an awaitable object
 - The object must be awaitable, being especially made for the asyncio library

Example:
```python
async def print_after(delay, msg):
    await asyncio.sleep(delay)
    print (msg)
```
 
### asyncio.gather()
 - The gather function can take several coroutines as its input, and run them concurrently
 
 Example:
```python
await asyncio.gather(say_hello(), do_something_else())`
```
 
### More information
 - [@moraneus/mastering-pythons-asyncio-a-practical-guide](https://medium.com/@moraneus/mastering-pythons-asyncio-a-practical-guide-0a673265cf04)
