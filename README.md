# BigDecimal

BigDecimal is an arbitrary precision floating point number class.

Like other floating point number implementations, it stores a Mantissa and an Exponent.
The difference is, these values are of type BigInteger, and so can be arbitrary precision.
<br /><br />
  :new: Now supports logarithms and trigonometric functions:
LogN, Ln, Log2, Log10, Exp, Sin, Cos, Tan, Cot, Sec, Csc, Sinh, Cosh, Tanh, Coth, Sech, Csch, Arcsin, Arccos, Arctan, Arccot, Arccsc
<br /><br />
  :arrow_down: [Download the latest package from NuGet](https://www.nuget.org/packages/ExtendedNumerics.BigDecimal) if you just want the compiled binaries. You can either include the nuget package in your project outright, or extract the assembly .dll from the nuget package. (Explaination: A .nupkg file is just a .zip file renamed. Use 7zip to extract the binaries from it.): 
<br /><br />
  :interrobang:	[See the Documentation Wiki Page](https://github.com/AdamWhiteHat/BigDecimal/wiki/Documentation) for important information on correct and accurate usage, tips and other information.
<br /><br />
  :left_speech_bubble: [Visit the community discussion forums](https://github.com/AdamWhiteHat/BigDecimal/discussions) if you have a question or want to start a discussion relevant to the this project. 
<br /><br />
  :cockroach: [View out open issues](https://github.com/AdamWhiteHat/BigDecimal/issues) if you are experiencing a bug or have an idea for a new feature. You can also discuss new feature ideas in the [discussion](https://github.com/AdamWhiteHat/BigDecimal/discussions) forums first. An 'issue' for the new feature can be created from a discussion at any time.

 
<br /><br />

Example usage:
```csharp
Console.WriteLine(BigDecimal.Precision);
// 5000
BigDecimal.Precision = 200; // Tone down the precision for this demo.
Console.WriteLine(BigDecimal.Precision);
// 200

BigDecimal goldenRatio = BigDecimal.Divide(BigDecimal.Add(BigDecimal.One, BigDecimal.Pow(5d, 0.5d)), BigDecimal.Parse("2"));
BigDecimal almostInteger = BigDecimal.Pow(goldenRatio, 23);
Console.WriteLine(almostInteger);
// 64079.00001560578384383500959972260039151833845477140599206350517199794937295147270152942235863491540475774000502741633359451934934882489092137272096824676971700933979751496900324221635899408750483174158953011851250910101237515143968376713756637230312138443375432324556317247823731646925119584432357765294362228759928426416872990657055876547580521657363887865665906948418349

Console.WriteLine(almostInteger.Mantissa);
// 6407900001560578384383500959972260039151833845477140599206350517199794937295147270152942235863491540475774000502741633359451934934882489092137272096824676971700933979751496900324221635899408750483174158953011851250910101237515143968376713756637230312138443375432324556317247823731646925119584432357765294362228759928426416872990657055876547580521657363887865665906948418349
Console.WriteLine(almostInteger.Exponent);
// -368

BigDecimal X = BigDecimal.Parse("0.000551876379690949227373068432671081677704194260485651214128035320088300220750");
Console.WriteLine(X);
// 0.00055187637969094922737306843267108167770419426048565121412803532008830022075

BigDecimal result = BigDecimal.Divide(BigDecimal.One, X);
Console.WriteLine(result);
// 1812.000000000000000000000000000000000000000000000000000000000000000000000001812000000000000000000000000000000000000000000000000000000000000000000000001812000000000000000000000000000000000000000000000000000000000000000000000001

```



#

# Other mathy projects & numeric types

I've written a number of other polynomial implementations and numeric types catering to various specific scenarios. Depending on what you're trying to do, another implementation of this same library might be more appropriate. All of my polynomial projects should have feature parity, where appropriate[^1].

[^1]: For example, the ComplexPolynomial implementation may be missing certain operations (namely: Irreducibility), because such a notion does not make sense or is ill defined in the context of complex numbers).

* [GenericArithmetic](https://github.com/AdamWhiteHat/GenericArithmetic) - A core math library. Its a class of static methods that allows you to perform arithmetic on an arbitrary numeric type, represented by the generic type T, who's concrete type is decided by the caller. This is implemented using System.Linq.Expressions and reflection to resolve the type's static overloadable operator methods at runtime, so it works on all the .NET numeric types automagically, as well as any custom numeric type, provided it overloads the numeric operators and standard method names for other common functions (Min, Max, Abs, Sqrt, Parse, Sign, Log,  Round, etc.). Every generic arithmetic class listed below takes a dependency on this class.

* [Polynomial](https://github.com/AdamWhiteHat/Polynomial) - The original. A univariate polynomial that uses System.Numerics.BigInteger as the indeterminate type.
* [GenericPolynomial](https://github.com/AdamWhiteHat/GenericPolynomial) -  A univariate polynomial library that allows the indeterminate to be of an arbitrary type, as long as said type implements operator overloading. This is implemented dynamically, at run time, calling the operator overload methods using Linq.Expressions and reflection.
* [CSharp11Preview.GenericMath.Polynomial](https://github.com/AdamWhiteHat/CSharp11Preview.GenericMath.Polynomial) -  A univariate polynomial library that allows the indeterminate to be of an arbitrary type, but this version is implemented using C# 11's new Generic Math via static virtual members in interfaces.
>
* [MultivariatePolynomial](https://github.com/AdamWhiteHat/MultivariatePolynomial) - A multivariate polynomial (meaning more than one indeterminate, e.g. 2*X*Y^2) which uses BigInteger as the type for the indeterminates.
* [GenericMultivariatePolynomial](https://github.com/AdamWhiteHat/GenericMultivariatePolynomial) - A multivariate polynomial that allows the indeterminates to be of [the same] arbitrary type. GenericMultivariatePolynomial is to MultivariatePolynomial what GenericPolynomial is to Polynomial, and indeed is implemented using the same strategy as GenericPolynomial (i.e. dynamic calling of the operator overload methods at runtime using Linq.Expressions and reflection).
>
* [ComplexPolynomial](https://github.com/AdamWhiteHat/ComplexPolynomial) - A univariate polynomial library that has System.Numerics.Complex type indeterminates.
* [ComplexMultivariatePolynomial](https://github.com/AdamWhiteHat/ComplexMultivariatePolynomial) -  A multivariate polynomial library that has System.Numerics.Complex indeterminates.
>
* [BigDecimal](https://github.com/AdamWhiteHat/BigDecimal) - An arbitrary precision, base-10 floating point number class.
* [BigRational](https://github.com/AdamWhiteHat/BigRational) - Encodes a numeric value as an Integer + Fraction
* [BigComplex](https://github.com/AdamWhiteHat/BigComplex) - Essentially the same thing as System.Numerics.Complex but uses a System.Numerics.BigInteger type for the real and imaginary parts instead of a double.
>
* [IntervalArithmetic](https://github.com/AdamWhiteHat/IntervalArithmetic). Instead of representing a value as a single number, interval arithmetic represents each value as a mathematical interval, or range of possibilities, [a,b], and allows the standard arithmetic operations to be performed upon them too, adjusting or scaling the underlying interval range as appropriate. See [Wikipedia's article on Interval Arithmetic](https://en.wikipedia.org/wiki/Interval_arithmetic) for further information.
* [GNFS](https://github.com/AdamWhiteHat/GNFS) - A C# reference implementation of the General Number Field Sieve algorithm for the purpose of better understanding the General Number Field Sieve algorithm.
