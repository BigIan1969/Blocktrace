# Blocktrace
Utility to enable blockchain verification of a programmes execution trace.  Essentially providing a verifiable evidence chain that a method executed at a specific time and that it behaved as expected (verifiable externally and automatically)

#Example

An example that traces a simple fibonacci function

      from blocktrace import blocktrace

      #Demo function to trace
      def fib(n):
          i, f1, f2 = 1, 1, 1
          while i < n:
              f1, f2 = f2, f1 + f2
              i += 1
          return f1

      #Instanciate blocktrace tracking changes on globals and builtins but tracing all local variables regardless of changes
      example=blocktrace.BlockTrace("Test",_globals='changes',_locals="on",_builtins="changes")

      #Start tracing
      example.start()
      
      #Execute function you want to trace
      fib(3)
      
      #Stop tracing
      example.stop()
      
      #In this example we'll just print out the block chain
      print(example.block)
