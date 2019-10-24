---
title: Kontrolní výrazy ve spravovaném kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 529c19753d09d6335e5c9fc5e839cdb7cd0c118c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745780"
---
# <a name="assertions-in-managed-code"></a>Kontrolní výrazy ve spravovaném kódu
Kontrolní výraz nebo příkaz `Assert` testuje podmínku, kterou zadáte jako argument pro příkaz `Assert`. Pokud je podmínka vyhodnocena jako true, nedojde k žádné akci. Pokud je podmínka vyhodnocena jako false, kontrolní výraz se nezdařil. Pokud používáte se sestavením pro ladění, program přejde do režimu přerušení.

## <a name="BKMK_In_this_topic"></a>V tomto tématu
 [Výrazy v oboru názvů System. Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Metoda Debug. Assert](#BKMK_The_Debug_Assert_method)

 [Vedlejší účinky příkazu Debug. Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Požadavky na trasování a ladění](#BKMK_Trace_and_Debug_Requirements)

 [Argumenty kontrolního výrazu](#BKMK_Assert_arguments)

 [Přizpůsobení chování kontrolního výrazu](#BKMK_Customizing_Assert_behavior)

 [Nastavení kontrolních výrazů v konfiguračních souborech](#BKMK_Setting_assertions_in_configuration_files)

## <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a>Výrazy v oboru názvů System. Diagnostics
 V Visual Basic a vizuálu C#můžete použít metodu `Assert` z <xref:System.Diagnostics.Debug> nebo <xref:System.Diagnostics.Trace>, které jsou v oboru názvů <xref:System.Diagnostics>. metody třídy <xref:System.Diagnostics.Debug> nejsou součástí verze programu, takže nezvyšují velikost ani neomezují rychlost kódu vydání.

 C++nepodporuje metody třídy <xref:System.Diagnostics.Debug>. Stejný efekt můžete dosáhnout pomocí <xref:System.Diagnostics.Trace> třídy s podmínkou kompilace, jako je například `#ifdef DEBUG`...  `#endif`.

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_The_Debug_Assert_method"></a>Metoda Debug. Assert
 Použijte metodu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> volně k testování podmínek, které by měly držet hodnotu true, pokud je váš kód správný. Předpokládejme například, že jste napsali funkci dělení celého čísla. Podle pravidel matematického dělitele nemůže nikdy být nula. Můžete ho otestovat pomocí kontrolního výrazu:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
    { Debug.Assert ( divisor != 0 );
        return ( dividend / divisor ); }
```

 Při spuštění tohoto kódu v rámci ladicího programu je vyhodnocen příkaz kontrolního výrazu, ale ve verzi Release není porovnání provedeno, takže nedochází k žádné další režii.

 Tady je další příklad. Máte třídu, která implementuje kontrolní účet, a to následujícím způsobem:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Debug.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Debug.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Před tím, než z účtu odeberete peníze, se ujistěte, že je zůstatek účtu dostačující k pokrytí množství, které připravujete ke stažení. Je možné napsat kontrolní výraz pro kontrolu zůstatku:

```VB
Dim amount, balance As Double
balance = savingsAccount.balance
Trace.Assert(amount <= balance)
SavingsAccount.Withdraw(amount)
```

```csharp
float balance = savingsAccount.Balance;
Trace.Assert ( amount <= balance );
savingsAccount.Withdraw ( amount );
```

 Všimněte si, že volání metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> zmizí při vytváření verze kódu. To znamená, že volání, které kontroluje zůstatek, zmizí ve vydané verzi. Chcete-li tento problém vyřešit, nahraďte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, které nezmizí v této vydané verzi:

 Volání <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> přidání režie do verze vydaných verzí, na rozdíl od volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Side_effects_of_Debug_Assert"></a>Vedlejší účinky příkazu Debug. Assert
 Při použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> se ujistěte, že veškerý kód v rámci `Assert` nemění výsledky programu, pokud je `Assert` odebraný. V opačném případě může dojít k náhodnému zavedení chyby, která se zobrazí pouze v prodejní verzi programu. Buďte obzvláště opatrní na kontrolní výrazy, které obsahují volání funkce nebo procedury, jako je například následující příklad:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Toto použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> se může na první pohled jevit jako bezpečné, ale Předpokládejme, že funkce pro aktualizaci čítače pokaždé, když se zavolá. Při sestavování vydání verze se toto volání metody oznamující eliminuje, takže se čítač neaktualizuje. Toto je příklad funkce s vedlejším účinkem. Zrušení volání funkce, která má vedlejší účinky, může způsobit chybu, která se zobrazí pouze ve vydané verzi. Chcete-li se těmto problémům vyhnout, neumísťují volání funkcí do příkazu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>. Místo toho použijte dočasnou proměnnou:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 I když použijete <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, můžete přesto chtít zabránit umístění volání funkcí do příkazu `Assert`. Taková volání by měla být bezpečná, protože příkazy <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> nejsou v sestavení pro vydání eliminovány. Pokud se však těmto konstrukcím vyhnete ve věcech stat, je pravděpodobně při použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> chyba udělat.

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Trace_and_Debug_Requirements"></a>Požadavky na trasování a ladění
 Pokud vytvoříte projekt pomocí průvodců [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], symbol trasování je ve výchozím nastavení definován v konfiguraci vydávání i ladění. Symbol ladění je ve výchozím nastavení definován pouze v sestavení ladění.

 Jinak, aby <xref:System.Diagnostics.Trace> metody fungovaly, musí mít program jednu z následujících možností v horní části zdrojového souboru:

- `#Const TRACE = True` v Visual Basic

- `#define TRACE` v vizuálu C# aC++

  Nebo program musí být sestaven s možností trasování:

- `/d:TRACE=True` v Visual Basic

- `/d:TRACE` v vizuálu C# aC++

  Pokud potřebujete použít metody ladění v sestavení verze C# nebo Visual Basic, je nutné v konfiguraci vydané verze definovat symbol ladění.

  C++nepodporuje metody třídy <xref:System.Diagnostics.Debug>. Stejný efekt můžete dosáhnout pomocí <xref:System.Diagnostics.Trace> třídy s podmínkou kompilace, jako je například `#ifdef DEBUG`...  `#endif`. Tyto symboly lze definovat v dialogovém okně **\<Project > stránky vlastností** . Další informace naleznete v tématu [Změna nastavení projektu pro Visual Basic konfigurace ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) nebo [Změna nastavení projektu pro konfiguraci jazyka C nebo C++ ladění](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="BKMK_Assert_arguments"></a>Argumenty kontrolního výrazu
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> přebírají až tři argumenty. První argument, který je povinný, je podmínka, kterou chcete kontrolovat. Pokud zavoláte <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> pouze s jedním argumentem, metoda `Assert` zkontroluje podmínku a, pokud je výsledek false, vypíše obsah zásobníku volání do okna **výstup** . Následující příklad ukazuje <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Druhý a třetí argument, pokud je přítomen, musí být řetězce. Pokud zavoláte <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> se dvěma nebo třemi argumenty, první argument je podmínka. Metoda zkontroluje podmínku a, pokud je výsledek false, vypíše druhý řetězec a třetí řetězce. Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> použity se dvěma argumenty:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert%2A> a <xref:System.Diagnostics.Trace.Assert%2A>:

```VB
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )
```

```csharp
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );
```

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Customizing_Assert_behavior"></a>Přizpůsobení chování kontrolního výrazu
 Pokud spouštíte aplikaci v režimu uživatelského rozhraní, metoda `Assert` zobrazí dialogové okno **neúspěšného kontrolního výrazu** , pokud se podmínka nezdařila. Akce, ke kterým dochází, když je kontrolní výraz neúspěšný, je řízen vlastností <xref:System.Diagnostics.Debug.Listeners%2A> nebo <xref:System.Diagnostics.Trace.Listeners%2A>.

 Chování výstupu můžete přizpůsobit přidáním objektu <xref:System.Diagnostics.TraceListener> do kolekce `Listeners`, odebráním <xref:System.Diagnostics.TraceListener> z kolekce `Listeners` nebo přepsáním metody <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> stávajícího `TraceListener`, aby se chovala jinak.

 Můžete například přepsat metodu <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> pro zápis do protokolu událostí namísto zobrazení dialogového okna **kontrolního výrazu, který se nezdařil** .

 Chcete-li výstup přizpůsobit tímto způsobem, musí váš program obsahovat naslouchací proces a je nutné dědit z <xref:System.Diagnostics.TraceListener> a přepsat jeho <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodu.

 Další informace naleznete v tématu [Trace Listeners](/dotnet/framework/debug-trace-profile/trace-listeners).

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="BKMK_Setting_assertions_in_configuration_files"></a>Nastavení kontrolních výrazů v konfiguračních souborech
 Kontrolní výrazy můžete nastavit v konfiguračním souboru programu a také ve vašem kódu. Další informace naleznete v tématech <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)