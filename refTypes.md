# Reference Types
Based on: https://www.baeldung.com/java-reference-types
Reference Type:   | Hard / Strong          | Soft                            | Weak                                            | Phantom
---               | ---                    | ---                             | ---                                             | ---
Brief description | default                | memory protection               | canonicalizing mappings                         | fine-grained finalization
Creation          | `new T()`              | `new SoftReference<T>(new T())` | `new WeakReference<T>(new T())`                 | `new PhantomReference<T>(new T(), new ReferenceQueue<T>())`
GC collection     | `null` &rarr; possible | possible                        | direct                                          | direct
GC finalization   | possible               | before OOME                     | direct                                          | manually using a `ReferenceQueue`
Get referent      | itself                 | `get()` and null-check          | - via HardRef <br/> - `get()` and null-check    | - via HardRef <br/> - extend `PhantomReference` with own cleanup logic
Usage             | general purpose        | caches                          | canonicalizing mappings (`WeakHashMap`)         | - as a better alternative to `Object.finalize()` <br/> - debugging <br/> - memory leak detection <br/> - GC observation
