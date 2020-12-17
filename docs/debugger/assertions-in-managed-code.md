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
ms.openlocfilehash: 824c711fc0ebb26a78338a65808c6fdbed768919
ms.sourcegitcommit: fed8782b2fb2ca18a90746b6e7e0b33f3fde10f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/17/2020
ms.locfileid: "97646395"
---
# <a name="assertions-in-managed-code"></a>Kontrolní výrazy ve spravovaném kódu
Kontrolní příkaz – neboli příkaz `Assert` – testuje podmínku, kterou zadáte jako argument příkazu `Assert`. Pokud je tato podmínka vyhodnocena jako true, nedojde k žádné akci. Pokud je tato podmínka vyhodnocena jako false, kontrola selže. Pokud máte spuštěný build pro ladění, program přejde do režimu pozastavení.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 [Výrazy v oboru názvů System. Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)

 [Metoda Debug. Assert](#BKMK_The_Debug_Assert_method)

 [Vedlejší účinky příkazu Debug. Assert](#BKMK_Side_effects_of_Debug_Assert)

 [Požadavky na trasování a ladění](#BKMK_Trace_and_Debug_Requirements)

 [Argumenty kontrolního výrazu](#BKMK_Assert_arguments)

 [Přizpůsobení chování kontrolního výrazu](#BKMK_Customizing_Assert_behavior)

 [Nastavení kontrolních výrazů v konfiguračních souborech](#BKMK_Setting_assertions_in_configuration_files)

## <a name="asserts-in-the-systemdiagnostics-namespace"></a><a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Výrazy v oboru názvů System. Diagnostics
 V Visual Basic a Visual C# lze použít `Assert` metodu z <xref:System.Diagnostics.Debug> nebo <xref:System.Diagnostics.Trace> , která jsou v <xref:System.Diagnostics> oboru názvů. Metody třídy <xref:System.Diagnostics.Debug> nejsou zahrnuty ve vydané verzi vašeho programu, takže nezvyšují velikost ani nesnižují rychlost kódu vydané verze.

 Jazyk C++ nepodporuje <xref:System.Diagnostics.Debug> metody třídy. Stejný efekt lze dosáhnout použitím <xref:System.Diagnostics.Trace> třídy s podmínkou kompilace, například `#ifdef DEBUG` ... `#endif` .

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="the-debugassert-method"></a><a name="BKMK_The_Debug_Assert_method"></a> Metoda Debug. Assert
 Použijte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metodu volně k testování podmínek, které by měly držet hodnotu true, pokud je váš kód správný. Předpokládejme například, že jste napsali funkci pro dělení celých čísel. Podle matematických pravidel nemůže být dělitel nikdy nula. Můžete to otestovat pomocí kontrolního příkazu:

```VB
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer
    Debug.Assert(divisor <> 0)
    Return CInt(dividend / divisor)
End Function
```

```csharp
int IntegerDivide ( int dividend , int divisor )
{
    Debug.Assert ( divisor != 0 );
    return ( dividend / divisor );
}
```

 Když spustíte tento kód v ladicím programu, je kontrolní příkaz vyhodnocen, ale ve vydané verzi se toto porovnání neprovádí, takže nedochází k žádnému dodatečnému zatížení.

 Zde je další příklad. Máte třídu, která implementuje kontrolní účet, a to následujícím způsobem:

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

 Všimněte si, že volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metody zmizí při vytvoření vydané verze kódu. To znamená, že volání, které kontroluje zůstatek, zmizí ve vydané verzi. Chcete-li tento problém vyřešit, nahraďte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> pomocí <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> , který ve vydané verzi nezmizí:

 Volání pro <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> Přidání režie do verze vydaných verzí, na rozdíl od volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="side-effects-of-debugassert"></a><a name="BKMK_Side_effects_of_Debug_Assert"></a> Vedlejší účinky příkazu Debug. Assert
 Pokud použijete <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> , ujistěte se, že veškerý kód v rámci `Assert` nemění výsledky programu, pokud `Assert` je odebrán. Jinak byste mohli náhodně zavést chybu, která se projeví pouze ve vydané verzi vašeho programu. Buďte obzvláště opatrní na kontrolní výrazy, které obsahují volání funkce nebo procedury, jako je například následující příklad:

```VB
' unsafe code
Debug.Assert (meas(i) <> 0 )
```

```csharp
// unsafe code
Debug.Assert (meas(i) != 0 );
```

 Toto použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> může být na první pohled bezpečné, ale v případě, že je funkce přidaná, při každém volání aktualizuje čítač. Při sestavování vydání verze se toto volání metody oznamující eliminuje, takže se čítač neaktualizuje. Toto je příklad funkce s vedlejším účinkem. Zrušení volání funkce, která má vedlejší účinky, může způsobit chybu, která se zobrazí pouze ve vydané verzi. Chcete-li se těmto problémům vyhnout, neumísťují volání funkcí do <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> příkazu. Místo toho použijte dočasnou proměnnou:

```VB
temp = meas( i )
Debug.Assert (temp <> 0)
```

```csharp
temp = meas( i );
Debug.Assert ( temp != 0 );
```

 I v případě, že použijete <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> , můžete přesto chtít zabránit umístění volání funkcí do `Assert` příkazu. Taková volání by měla být bezpečná, protože <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> příkazy nejsou v buildu pro vydání eliminovány. Pokud se však těmto konstrukcím vyhnete ve věcech stat, je pravděpodobně při použití chyba udělat chybu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> .

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="trace-and-debug-requirements"></a><a name="BKMK_Trace_and_Debug_Requirements"></a> Požadavky na trasování a ladění
 Pokud vytvoříte projekt pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] průvodců, je symbol trasování definován ve výchozím nastavení v konfiguraci vydávání i ladění. Symbol ladění je ve výchozím nastavení definován pouze v sestavení ladění.

 Jinak, aby <xref:System.Diagnostics.Trace> metody fungovaly, musí mít program jednu z následujících v horní části zdrojového souboru:

- `#Const TRACE = True` v Visual Basic

- `#define TRACE` v jazyce Visual C# a C++

  Nebo program musí být sestaven s možností trasování:

- `/d:TRACE=True` v Visual Basic

- `/d:TRACE` v jazyce Visual C# a C++

  Pokud potřebujete použít metody ladění v sestavení verze C# nebo Visual Basic, je nutné v konfiguraci vydané verze definovat symbol ladění.

  Jazyk C++ nepodporuje <xref:System.Diagnostics.Debug> metody třídy. Stejný efekt lze dosáhnout použitím <xref:System.Diagnostics.Trace> třídy s podmínkou kompilace, například `#ifdef DEBUG` ... `#endif` . Tyto symboly lze definovat v dialogovém okně **\<Project> stránky vlastností** . Další informace naleznete v tématu [Změna nastavení projektu pro Visual Basic konfigurace ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) nebo [Změna nastavení projektu pro konfiguraci ladění jazyka C nebo C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

## <a name="assert-arguments"></a><a name="BKMK_Assert_arguments"></a> Argumenty kontrolního výrazu
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> Vezměte až tři argumenty. První argument, který je povinný, je podmínka, kterou chcete kontrolovat. Pokud voláte <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> pouze jeden argument, `Assert` Metoda zkontroluje podmínku a, pokud je výsledek false, vypíše obsah zásobníku volání do okna **výstup** . Následující příklad ukazuje <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> :

```VB
Debug.Assert(stacksize > 0)
Trace.Assert(stacksize > 0)
```

```csharp
Debug.Assert ( stacksize > 0 );
Trace.Assert ( stacksize > 0 );
```

 Druhý a třetí argument, pokud je přítomen, musí být řetězce. Pokud voláte <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> se dvěma nebo třemi argumenty, první argument je podmínka. Metoda zkontroluje podmínku a, pokud je výsledek false, vypíše druhý řetězec a třetí řetězce. Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> používá se dvěma argumenty:

```VB
Debug.Assert(stacksize > 0, "Out of stack space")
Trace.Assert(stacksize > 0, "Out of stack space")
```

```csharp
Debug.Assert ( stacksize > 0, "Out of stack space" );
Trace.Assert ( stacksize > 0, "Out of stack space" );
```

 Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert%2A> a <xref:System.Diagnostics.Trace.Assert%2A> :

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

## <a name="customizing-assert-behavior"></a><a name="BKMK_Customizing_Assert_behavior"></a> Přizpůsobení chování kontrolního výrazu
 Spouštíte-li aplikaci v režimu uživatelského rozhraní, `Assert` Metoda zobrazí dialogové okno **neúspěšného kontrolního výrazu** , pokud se podmínka nezdařila. Akce, ke kterým dochází, když je kontrolní výraz neúspěšný, je řízen <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> vlastností or.

 Chování výstupu můžete přizpůsobit přidáním <xref:System.Diagnostics.TraceListener> objektu do `Listeners` kolekce, odebráním <xref:System.Diagnostics.TraceListener> z `Listeners` kolekce nebo přepsáním <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody existující, `TraceListener` aby se chovala jinak.

 Můžete například přepsat <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodu pro zápis do protokolu událostí namísto zobrazení dialogového okna **kontrolního výrazu, který se nezdařil** .

 Chcete-li výstup přizpůsobit tímto způsobem, musí váš program obsahovat naslouchací proces a je nutné zdědit z <xref:System.Diagnostics.TraceListener> a přepsat jeho <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metodu.

 Další informace naleznete v tématu [Trace Listeners](/dotnet/framework/debug-trace-profile/trace-listeners).

 [V tomto tématu](#BKMK_In_this_topic)

## <a name="setting-assertions-in-configuration-files"></a><a name="BKMK_Setting_assertions_in_configuration_files"></a> Nastavení kontrolních výrazů v konfiguračních souborech
 Kontrolní výrazy můžete nastavit v konfiguračním souboru programu a také ve vašem kódu. Další informace naleznete v tématech <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>
- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Postupy: Podmíněná kompilace pomocí atributu Trace a Debug](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)