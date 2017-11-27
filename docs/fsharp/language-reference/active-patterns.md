---
title: Aktive Muster (F#)
description: Erfahren Sie, wie mit aktiven Mustern verwenden, um benannte Partitionen definieren, die Eingabedaten in der Programmiersprache f# zu unterteilen.
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 11a724ff-f9ff-4056-b5e0-87e9ed986f4a
ms.openlocfilehash: 845184e6150cf0b93393038ca3d39f0e6d898a2e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="active-patterns"></a><span data-ttu-id="c92ce-104">Aktive Muster</span><span class="sxs-lookup"><span data-stu-id="c92ce-104">Active Patterns</span></span>

<span data-ttu-id="c92ce-105">*Aktive Muster* ermöglichen es Ihnen, definieren benannte Partitionen, die Eingabedaten zu unterteilen, damit Sie diese Namen in einem Mustervergleichsausdruck wie für eine Unterscheidungs-Union verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c92ce-105">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="c92ce-106">Mit aktiven Mustern können Sie Daten benutzerdefiniert für jede Partition zerlegen.</span><span class="sxs-lookup"><span data-stu-id="c92ce-106">You can use active patterns to decompose data in a customized manner for each partition.</span></span>


## <a name="syntax"></a><span data-ttu-id="c92ce-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c92ce-107">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="c92ce-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c92ce-108">Remarks</span></span>
<span data-ttu-id="c92ce-109">In der vorherigen Syntax sind die Bezeichner Namen für Partitionen der Eingabedaten, die von dargestellte *Argumente*, oder in anderen Worten: die Namen für Teilmengen der Menge aller Werte der Argumente.</span><span class="sxs-lookup"><span data-stu-id="c92ce-109">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="c92ce-110">Es kann bis zu sieben Partitionen in der Definition eines aktiven Musters vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="c92ce-110">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="c92ce-111">Die *Ausdruck* beschreibt die Form, in der die Daten zerlegt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c92ce-111">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="c92ce-112">Definition eines aktiven Musters können Sie definieren die Regeln zum bestimmen, welche benannten Partitionen die Werte, die als Argumente zu gehören.</span><span class="sxs-lookup"><span data-stu-id="c92ce-112">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="c92ce-113">Der (| und |) Symbole werden als bezeichnet *Bananenklammern* und die Funktion erstellt, die von diesem Typ der Let-Bindung wird ein *aktive Erkennung*.</span><span class="sxs-lookup"><span data-stu-id="c92ce-113">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="c92ce-114">Beispielsweise sollten Sie die folgenden aktive Muster mit einem Argument.</span><span class="sxs-lookup"><span data-stu-id="c92ce-114">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="c92ce-115">Sie können das aktive Muster in einem Mustervergleichsausdruck wie im folgenden Beispiel gezeigt verwenden.</span><span class="sxs-lookup"><span data-stu-id="c92ce-115">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="c92ce-116">Die Ausgabe dieses Programms lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-116">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="c92ce-117">Eine weitere Verwendungsmöglichkeit der aktive Muster ist zum Zerlegen von Datentypen auf verschiedene Weise, wie z. B. wenn die gleichen zugrunde liegenden Daten verschiedene mögliche Darstellungen aufweist.</span><span class="sxs-lookup"><span data-stu-id="c92ce-117">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="c92ce-118">Angenommen, ein `Color` Objekt konnte in eine RGB-Darstellung oder eine HSB-Darstellung zerlegt werden.</span><span class="sxs-lookup"><span data-stu-id="c92ce-118">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="c92ce-119">Die Ausgabe des oben genannten Programms lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-119">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="c92ce-120">In Kombination diese beiden Methoden mit aktiven Mustern ermöglichen Ihnen eine Partition Daten in der entsprechenden Format zerlegen und führen Sie die entsprechenden Berechnungen auf die entsprechenden Daten in der für die Berechnung am einfachsten Form.</span><span class="sxs-lookup"><span data-stu-id="c92ce-120">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="c92ce-121">Die resultierende Muster übereinstimmende Ausdrücke aktivieren Daten auf einfache Weise geschrieben werden, die schwer lesbar, erheblich vereinfachen potenziell komplexen Verzweigen und Datencode für die Analyse ist.</span><span class="sxs-lookup"><span data-stu-id="c92ce-121">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>


## <a name="partial-active-patterns"></a><span data-ttu-id="c92ce-122">Partielle aktive Muster</span><span class="sxs-lookup"><span data-stu-id="c92ce-122">Partial Active Patterns</span></span>
<span data-ttu-id="c92ce-123">In einigen Fällen müssen Sie nur einen Teil der Eingabe Speicherplatz zu partitionieren.</span><span class="sxs-lookup"><span data-stu-id="c92ce-123">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="c92ce-124">In diesem Fall schreiben Sie einen Satz von partiellen Mustern, von denen mit einigen Eingaben übereinstimmt, aber nicht andere Eingaben entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c92ce-124">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="c92ce-125">Aktive Muster, die immer keinen Wert zurückgibt, heißen *partielle aktive Muster*; sie haben einen Rückgabewert, der ein Optionstyp ist.</span><span class="sxs-lookup"><span data-stu-id="c92ce-125">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="c92ce-126">Um eine partielle aktive Muster zu definieren, verwenden Sie ein Platzhalterzeichen (_) am Ende der Liste von Mustern innerhalb der Bananenklammern.</span><span class="sxs-lookup"><span data-stu-id="c92ce-126">To define a partial active pattern, you use a wildcard character (_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="c92ce-127">Der folgende Code veranschaulicht die Verwendung eines partiellen aktiven Musters.</span><span class="sxs-lookup"><span data-stu-id="c92ce-127">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="c92ce-128">Die Ausgabe des vorherigen Beispiels lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-128">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="c92ce-129">Wenn Sie teilweise mit aktiven Mustern verwenden, können manchmal die einzelnen Optionen nicht zusammenhängenden oder sich gegenseitig ausschließende, jedoch müssen nicht sein.</span><span class="sxs-lookup"><span data-stu-id="c92ce-129">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="c92ce-130">Im folgenden Beispiel sind die Muster Square und Cube-Muster nicht zusammenhanglos, da einige Zahlen Quadrate und Cubes, z. B. 64 darstellen.</span><span class="sxs-lookup"><span data-stu-id="c92ce-130">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="c92ce-131">Das folgende Programm druckt alle ganzen Zahlen bis 1000000, die Quadrate und Cubes sind.</span><span class="sxs-lookup"><span data-stu-id="c92ce-131">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="c92ce-132">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-132">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="c92ce-133">Parametrisierte aktive Muster</span><span class="sxs-lookup"><span data-stu-id="c92ce-133">Parameterized Active Patterns</span></span>
<span data-ttu-id="c92ce-134">Aktive Muster akzeptieren immer mindestens ein Argument für das Element, das abgeglichen wird, aber möglicherweise nehmen sie weitere Argumente als auch in diesem Fall, dass der Name *parametrisierte aktives Muster* gilt.</span><span class="sxs-lookup"><span data-stu-id="c92ce-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="c92ce-135">Mit zusätzlichen Argumenten kann es sich um ein allgemeines Muster spezialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="c92ce-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="c92ce-136">Aktive Muster, die Verwendung von regulären Ausdrücken zum Analysieren von Zeichenfolgen häufig umfassen z. B. den regulären Ausdruck als zusätzlichen Parameter, wie im folgenden Code, der auch das partielle aktive Muster verwendet `Integer` im vorherigen Codebeispiel definiert.</span><span class="sxs-lookup"><span data-stu-id="c92ce-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="c92ce-137">In diesem Beispiel sind Zeichenfolgen, die regulären Ausdrücke für verschiedene Datumsformate verwenden angegeben, die allgemeine aktive Muster ParseRegex anpassen.</span><span class="sxs-lookup"><span data-stu-id="c92ce-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="c92ce-138">Aktive Integer-Muster wird verwendet, die übereinstimmenden Zeichenfolgen in ganze Zahlen konvertiert, die an den DateTime-Konstruktor übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="c92ce-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="c92ce-139">Die Ausgabe des vorherigen Codes lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="c92ce-140">Aktive Muster sind nicht nur auf übereinstimmende Ausdrücke das Muster beschränkt, Sie können diese auch für Let-Bindungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="c92ce-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="c92ce-141">Die Ausgabe des vorherigen Codes lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c92ce-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="c92ce-142">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c92ce-142">See Also</span></span>
[<span data-ttu-id="c92ce-143">F#-Sprachreferenz</span><span class="sxs-lookup"><span data-stu-id="c92ce-143">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c92ce-144">Vergleichsausdrücke</span><span class="sxs-lookup"><span data-stu-id="c92ce-144">Match Expressions</span></span>](match-expressions.md)
