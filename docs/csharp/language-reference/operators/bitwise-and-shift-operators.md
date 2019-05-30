---
title: 'Bitweise und Schiebeoperatoren: C#-Referenz'
description: Enthält Informationen zu C#-Operatoren, die bitweise bzw. Schiebeoperationen mit Operanden mit integralen Typen durchführen.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 65f7e2db176b408c9768ce73e297008c4b4c83d8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880615"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="74161-103">Bitweise und Schiebeoperatoren (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="74161-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="74161-104">Mit den folgenden Operatoren werden bitweise oder Schiebeoperationen mit Operanden durchgeführt, die [integrale Typen](../keywords/integral-types-table.md) aufweisen:</span><span class="sxs-lookup"><span data-stu-id="74161-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="74161-105">Unärer Operator [`~` (bitweises Komplement)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="74161-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="74161-106">Binäre Schiebeoperatoren [`<<` (Linksverschiebung)](#left-shift-operator-) und [`>>` (Rechtsverschiebung)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="74161-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="74161-107">Binäre Operatoren [`&` (logisches UND)](#logical-and-operator-), [`|` (logisches ODER)](#logical-or-operator-) und [`^` (logisches exklusives ODER)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="74161-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="74161-108">Diese Operatoren werden für die Typen `int`, `uint`, `long` und `ulong` definiert.</span><span class="sxs-lookup"><span data-stu-id="74161-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="74161-109">Wenn beide Operanden andere integrale Typen aufweisen (`sbyte`, `byte`, `short`, `ushort` oder `char`), werden ihre Werte in den Typ `int` konvertiert. Hierbei handelt es sich auch um den Ergebnistyp einer Operation.</span><span class="sxs-lookup"><span data-stu-id="74161-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="74161-110">Wenn die Operanden abweichende integrale Typen aufweisen, werden ihre Werte in den enthaltenden integralen Typ konvertiert, der am besten geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="74161-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="74161-111">Weitere Informationen finden Sie im Abschnitt [Numerische Heraufstufungen](~/_csharplang/spec/expressions.md#numeric-promotions) der [Spezifikation für die Sprache C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="74161-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="74161-112">Die Operatoren `&`, `|` und `^` werden auch für die Operanden des Typs `bool` definiert.</span><span class="sxs-lookup"><span data-stu-id="74161-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="74161-113">Weitere Informationen finden Sie unter [Logische boolesche Operatoren](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="74161-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="74161-114">Bitweise und Schiebeoperationen verursachen niemals Überläufe und führen sowohl in [geprüften als auch in ungeprüften](../keywords/checked-and-unchecked.md) Kontexten zu identischen Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="74161-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="74161-115">Bitweiser Komplementoperator ~</span><span class="sxs-lookup"><span data-stu-id="74161-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="74161-116">Mit dem Operator `~` wird ein bitweises Komplement seines Operanden erzeugt, indem jedes Bit umgekehrt wird:</span><span class="sxs-lookup"><span data-stu-id="74161-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="74161-117">Sie können das Symbol `~` auch verwenden, um Finalizers zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="74161-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="74161-118">Weitere Informationen finden Sie unter [Finalizer](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="74161-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="74161-119">Operator für Linksverschiebung \<\<</span><span class="sxs-lookup"><span data-stu-id="74161-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="74161-120">Mit dem Operator `<<` wird der erste Operand um die Anzahl von Bits nach links verschoben, die durch den zweiten Operanden angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="74161-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="74161-121">Bei der Operation zum Verschieben nach links werden die hohen Bits, die außerhalb des Bereichs des Ergebnistyps liegen, verworfen, und die niedrigen leeren Bitpositionen werden auf null festgelegt. Dies ist im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="74161-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="74161-122">Da die Verschiebeoperatoren nur für die Typen `int`, `uint`, `long` und `ulong` definiert werden, enthält das Ergebnis einer Operation immer mindestens 32 Bit.</span><span class="sxs-lookup"><span data-stu-id="74161-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="74161-123">Wenn der erste Operand einen abweichenden integralen Typ aufweist (`sbyte`, `byte`, `short`, `ushort` oder `char`), wird sein Wert in den Typ `int` konvertiert. Dies ist im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="74161-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="74161-124">Informationen dazu, wie der zweite Operand des Operators `<<` die Anzahl für die Verschiebung definiert, finden Sie im Abschnitt [Anzahl für die Verschiebung durch Schiebeoperatoren](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="74161-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="74161-125">Operator für Rechtsverschiebung >></span><span class="sxs-lookup"><span data-stu-id="74161-125">Right-shift operator >></span></span>

<span data-ttu-id="74161-126">Mit dem Operator `>>` wird der erste Operand um die Anzahl von Bits nach rechts verschoben, die durch den zweiten Operanden angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="74161-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="74161-127">Bei der Operation zum Verschieben nach rechts werden die niedrigen Bits verworfen. Dies ist im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="74161-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="74161-128">Die höheren leeren Bitpositionen werden basierend auf dem Typ des ersten Operanden wie folgt festgelegt:</span><span class="sxs-lookup"><span data-stu-id="74161-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="74161-129">Wenn der erste Operand vom Typ [int](../keywords/int.md) oder [long](../keywords/long.md) ist, führt der Operator zur Rechtsverschiebung eine *arithmetische* Verschiebung durch: Der Wert des Bits mit dem höchsten Stellenwert (MSB, „most significant bit“) des ersten Operanden wird auf die hohen leeren Bitpositionen übertragen.</span><span class="sxs-lookup"><span data-stu-id="74161-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="74161-130">Die hohen leeren Bitpositionen werden daher auf 0 festgelegt, wenn der erste Operand nicht negativ ist, bzw. auf 1, wenn der erste Operand negativ ist.</span><span class="sxs-lookup"><span data-stu-id="74161-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="74161-131">Wenn der erste Operand vom Typ [uint](../keywords/uint.md) oder [ulong](../keywords/ulong.md) ist, führt der Operator zur Rechtsverschiebung eine *logische* Verschiebung durch: Die hohen leeren Bitpositionen werden immer auf 0 (null) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="74161-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="74161-132">Informationen dazu, wie der zweite Operand des Operators `>>` die Anzahl für die Verschiebung definiert, finden Sie im Abschnitt [Anzahl für die Verschiebung durch Schiebeoperatoren](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="74161-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="74161-133">Logischer AND-Operator &amp;</span><span class="sxs-lookup"><span data-stu-id="74161-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="74161-134">Mit dem Operator `&` wird „bitweises logisches UND“ für die Operanden berechnet:</span><span class="sxs-lookup"><span data-stu-id="74161-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="74161-135">Für die Operanden vom Typ `bool` berechnet der Operator `&` [logisches UND](boolean-logical-operators.md#logical-and-operator-) für die Operanden.</span><span class="sxs-lookup"><span data-stu-id="74161-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="74161-136">Der unäre `&`-Operator ist der [address-of-Operator](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="74161-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="74161-137">Logischer exklusiver OR-Operator: ^</span><span class="sxs-lookup"><span data-stu-id="74161-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="74161-138">Mit dem Operator `^` wird „bitweises logisches exklusives ODER“, auch als „bitweises logisches XOR“ bezeichnet, seiner Operanden berechnet:</span><span class="sxs-lookup"><span data-stu-id="74161-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="74161-139">Für die Operanden vom Typ `bool` berechnet der Operator `^` [logisches exklusives ODER](boolean-logical-operators.md#logical-exclusive-or-operator-) für die Operanden.</span><span class="sxs-lookup"><span data-stu-id="74161-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="74161-140">Logischer OR-Operator: |</span><span class="sxs-lookup"><span data-stu-id="74161-140">Logical OR operator |</span></span>

<span data-ttu-id="74161-141">Mit dem Operator `|` wird „bitweises logisches ODER“ der Operanden berechnet:</span><span class="sxs-lookup"><span data-stu-id="74161-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="74161-142">Für die Operanden vom Typ `bool` berechnet der Operator `|` [logisches ODER](boolean-logical-operators.md#logical-or-operator-) für die Operanden.</span><span class="sxs-lookup"><span data-stu-id="74161-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="74161-143">Verbundzuweisung</span><span class="sxs-lookup"><span data-stu-id="74161-143">Compound assignment</span></span>

<span data-ttu-id="74161-144">Bei einem binären Operator `op` entspricht ein Verbundzuweisungsausdruck der Form</span><span class="sxs-lookup"><span data-stu-id="74161-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="74161-145">für die folgende Syntax:</span><span class="sxs-lookup"><span data-stu-id="74161-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="74161-146">außer dass `x` nur einmal überprüft wird.</span><span class="sxs-lookup"><span data-stu-id="74161-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="74161-147">Im folgenden Beispiel wird die Verwendung von Verbundzuweisungen mit bitweisen und Schiebeoperatoren veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="74161-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="74161-148">Aufgrund von [numerischen Höherstufungen](~/_csharplang/spec/expressions.md#numeric-promotions) kann das Ergebnis der Operation `op` ggf. nicht implizit in den Typ `T` von `x` konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="74161-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="74161-149">In diesem Fall gilt Folgendes: Wenn `op` ein vordefinierter Operator ist und das Ergebnis der Operation explizit in den Typ `T` von `x` konvertiert werden kann, entspricht ein Verbundzuweisungsausdruck der Form `x op= y` dem Ausdruck `x = (T)(x op y)`. Der einzige Unterschied ist, dass `x` nur einmal ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="74161-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="74161-150">Das folgende Beispiel veranschaulicht dieses Verhalten:</span><span class="sxs-lookup"><span data-stu-id="74161-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="74161-151">Operatorrangfolge</span><span class="sxs-lookup"><span data-stu-id="74161-151">Operator precedence</span></span>

<span data-ttu-id="74161-152">In der folgenden Liste sind die bitweisen und Schiebeoperatoren absteigend nach Rangfolge sortiert:</span><span class="sxs-lookup"><span data-stu-id="74161-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="74161-153">Bitweiser Komplementoperator `~`</span><span class="sxs-lookup"><span data-stu-id="74161-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="74161-154">Schiebeoperatoren `<<` und `>>`</span><span class="sxs-lookup"><span data-stu-id="74161-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="74161-155">Logischer AND-Operator `&`</span><span class="sxs-lookup"><span data-stu-id="74161-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="74161-156">Logischer exklusiver OR-Operator `^`</span><span class="sxs-lookup"><span data-stu-id="74161-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="74161-157">Logischer OR-Operator `|`</span><span class="sxs-lookup"><span data-stu-id="74161-157">Logical OR operator `|`</span></span>

<span data-ttu-id="74161-158">Verwenden Sie Klammern `()`, wenn Sie die Reihenfolge der Auswertung ändern möchten, die durch Operatorrangfolge festgelegt wird:</span><span class="sxs-lookup"><span data-stu-id="74161-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="74161-159">Die vollständige Liste der nach Rangfolgenebene sortierten C#-Operatoren finden Sie unter [C#-Operatoren](index.md).</span><span class="sxs-lookup"><span data-stu-id="74161-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="74161-160">Anzahl für die Verschiebung durch Schiebeoperatoren</span><span class="sxs-lookup"><span data-stu-id="74161-160">Shift count of the shift operators</span></span>

<span data-ttu-id="74161-161">Für die Schiebeoperatoren `<<` und `>>` muss der Typ des zweiten Operanden [int](../keywords/int.md) lauten oder ein Typ sein, der eine [vordefinierte implizite numerische Konvertierung](../keywords/implicit-numeric-conversions-table.md) in `int` aufweist.</span><span class="sxs-lookup"><span data-stu-id="74161-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="74161-162">Für die Ausdrücke `x << count` und `x >> count` hängt die tatsächliche Verschiebungsanzahl wie folgt vom Typ von `x` ab:</span><span class="sxs-lookup"><span data-stu-id="74161-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="74161-163">Lautet der Typ von `x` [int](../keywords/int.md) oder [uint](../keywords/uint.md), wird die Verschiebungsanzahl durch die niedrigen *fünf* Bits des zweiten Operanden definiert.</span><span class="sxs-lookup"><span data-stu-id="74161-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="74161-164">Die Verschiebungsanzahl errechnet sich daher aus `count & 0x1F` (oder `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="74161-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="74161-165">Lautet der Typ von `x` [long](../keywords/long.md) oder [ulong](../keywords/ulong.md), wird die Verschiebungsanzahl durch die niedrigen *sechs* Bits des zweiten Operanden definiert.</span><span class="sxs-lookup"><span data-stu-id="74161-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="74161-166">Die Verschiebungsanzahl errechnet sich daher aus `count & 0x3F` (oder `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="74161-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="74161-167">Das folgende Beispiel veranschaulicht dieses Verhalten:</span><span class="sxs-lookup"><span data-stu-id="74161-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="74161-168">Logische Enumerationsoperatoren</span><span class="sxs-lookup"><span data-stu-id="74161-168">Enumeration logical operators</span></span>

<span data-ttu-id="74161-169">Die Operatoren `~`, `&`, `|` und `^` werden auch für jeden [Enumerationstyp](../keywords/enum.md) definiert.</span><span class="sxs-lookup"><span data-stu-id="74161-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="74161-170">Für die Operanden mit dem gleichen Enumerationstyp wird eine logische Operation für die entsprechenden Werte des zugrunde liegenden integralen Typs durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="74161-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="74161-171">Für alle `x`- und `y`-Elemente des Enumerationstyps `T` mit dem zugrunde liegenden Typ `U` führt der Ausdruck `x & y` zum gleichen Ergebnis wie der Ausdruck `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="74161-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="74161-172">Normalerweise verwenden Sie bitweise logische Operatoren mit einem Enumerationstyp, der mit dem [Flags](xref:System.FlagsAttribute)-Attribut definiert wird.</span><span class="sxs-lookup"><span data-stu-id="74161-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="74161-173">Weitere Informationen finden Sie im Abschnitt [Enumerationstypen als Bitflags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) des Artikels [Enumerationstypen](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="74161-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="74161-174">Operatorüberladbarkeit</span><span class="sxs-lookup"><span data-stu-id="74161-174">Operator overloadability</span></span>

<span data-ttu-id="74161-175">Ein benutzerdefinierter Typ kann die Operatoren `~`, `<<`, `>>`, `&`, `|` und `^` [überladen](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="74161-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="74161-176">Wenn ein binärer Operator überladen ist, wird der zugehörige Verbundzuweisungsoperator implizit auch überladen.</span><span class="sxs-lookup"><span data-stu-id="74161-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="74161-177">Ein benutzerdefinierter Typ kann einen Verbundzuweisungsoperator nicht explizit überladen.</span><span class="sxs-lookup"><span data-stu-id="74161-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="74161-178">Wenn ein benutzerdefinierter Typ `T` den Operator `<<` oder `>>` überlädt, muss der Typ des ersten Operanden `T` und der Typ des zweiten Operanden `int` lauten.</span><span class="sxs-lookup"><span data-stu-id="74161-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="74161-179">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="74161-179">C# language specification</span></span>

<span data-ttu-id="74161-180">Weitere Informationen finden Sie in den folgenden Abschnitten der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="74161-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="74161-181">Bitweiser Komplementoperator</span><span class="sxs-lookup"><span data-stu-id="74161-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="74161-182">Shift operators (Schiebeoperatoren)</span><span class="sxs-lookup"><span data-stu-id="74161-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="74161-183">Logical operators (Logische Operatoren)</span><span class="sxs-lookup"><span data-stu-id="74161-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="74161-184">Verbundzuweisung</span><span class="sxs-lookup"><span data-stu-id="74161-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="74161-185">Numerische Heraufstufungen</span><span class="sxs-lookup"><span data-stu-id="74161-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="74161-186">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="74161-186">See also</span></span>

- [<span data-ttu-id="74161-187">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="74161-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="74161-188">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="74161-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="74161-189">C#-Operatoren</span><span class="sxs-lookup"><span data-stu-id="74161-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="74161-190">Logische boolesche Operatoren</span><span class="sxs-lookup"><span data-stu-id="74161-190">Boolean logical operators</span></span>](boolean-logical-operators.md)