---
title: let-Bindungen in Klassen (F#)
description: "Erfahren Sie, wie private Felder und private Funktionen für F#-Klassen, die mithilfe von 'let' Bindungen in der Klassendefinition definiert sind."
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a>let-Bindungen in Klassen

Sie können private Felder und private Funktionen für F#-Klassen definieren, mit `let` Bindungen in der Klassendefinition.


## <a name="syntax"></a>Syntax

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Hinweise
Die vorherige Syntax wird nach den Klassendeklarationen Überschrift und Vererbung, aber vor Memberdefinitionen angezeigt. Die Syntax gleicht der `let` Bindungen außerhalb von Klassen, aber die Namen in einer Klasse definiert ist, einen Bereich, auf die Klasse beschränkt ist. Ein `let` Bindung erstellt, ein privates Feld bzw. die Funktion; um Daten verfügbar zu machen oder Funktionen öffentlich, deklarieren Sie eine Eigenschaft oder ein Member-Methode.

Ein `let` Bindung, die sich nicht statisch ist eine Instanz aufgerufen `let` Bindung. Instanz `let` Bindungen ausgeführt, wenn Objekte erstellt werden. Statische `let` Bindungen sind Teil der statische Initialisierer für die Klasse, die unbedingt ausführen, bevor der Typ zuerst verwendet wird.

Der Code innerhalb der Instanz `let` den primären Konstruktor Parameter von Bindungen verwendet werden kann.

Attribute und Zugriffsmodifizierer sind zulässig, `let` Bindungen in Klassen.

Die folgenden Codebeispiele veranschaulichen verschiedene `let` Bindungen in Klassen.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Die Ausgabe lautet wie folgt.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternative Möglichkeiten zum Erstellen von Feldern
Sie können auch die `val` Schlüsselwort, um ein privates Feld erstellen. Bei Verwendung der `val` -Schlüsselwort, das Feld ist kein Wert zugewiesen, wenn das Objekt erstellt wird, sondern stattdessen mit einem Standardwert initialisiert wird. Weitere Informationen finden Sie unter [explizite Felder: das Val Schlüsselwort](explicit-fields-the-val-keyword.md).

Sie können auch private Felder in einer Klasse definieren, durch die Definition eines Elements verwenden und das Schlüsselwort hinzufügen `private` der Definition. Dies kann nützlich, wenn Sie erwarten, den Zugriff auf ein Element ändern dass, ohne den Code umzuschreiben sein. Weitere Informationen finden Sie unter [Zugriffssteuerung](../access-control.md).

## <a name="see-also"></a>Siehe auch
[Mitglieder](index.md)

[`do`-Bindungen in Klassen](do-bindings-in-classes.md)

[`let`Bindungen](../functions/let-bindings.md)
