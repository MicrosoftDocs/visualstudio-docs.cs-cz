---
title: Kontrolní výrazy ve spravovaném kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47b2b05ab358826d594d0c6ef29c1b50e0a529f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806539"
---
# <a name="assertions-in-managed-code"></a>Kontrolní výrazy ve spravovaném kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příslušný kontrolní výraz nebo `Assert` prohlášení, testuje podmínku, který zadáte jako argument `Assert` příkazu. Pokud je podmínka vyhodnocena jako true, nedojde k žádné akci. Pokud je podmínka vyhodnocena jako NEPRAVDA, výraz se nezdaří. Používáte-li sestavení pro ladění, váš program přejde do režimu přerušení.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Nepodmíněné výrazy v System.Diagnostics Namespace](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug.Assert – metoda](#BKMK_The_Debug_Assert_method)  
  
 [Vedlejší účinky Debug.Assert –](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Požadavky na ladění a trasování](#BKMK_Trace_and_Debug_Requirements)  
  
 [Assert – argumenty](#BKMK_Assert_arguments)  
  
 [Přizpůsobení chování Assert](#BKMK_Customizing_Assert_behavior)  
  
 [Kontrolní výrazy nastavení v konfiguračních souborech](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Nepodmíněné výrazy v System.Diagnostics Namespace  
 V jazyce Visual Basic a Visual C#, můžete použít `Assert` metoda buď z <xref:System.Diagnostics.Debug> nebo <xref:System.Diagnostics.Trace>, které jsou v <xref:System.Diagnostics> oboru názvů. <xref:System.Diagnostics.Debug> metody třídy nejsou součástí verze aplikace, tak dojít ke zvětšení nebo snížit rychlost verze kódu.  
  
 Jazyk C++ nepodporuje <xref:System.Diagnostics.Debug> metody třídy. Můžete stejného výsledku dosáhnout pomocí <xref:System.Diagnostics.Trace> třídy s podmíněné kompilace, jako například `#ifdef DEBUG`... `#endif`.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert – metoda  
 Použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoda volně k testování podmínek, které by měly mít hodnotu true, pokud váš kód je správný. Například předpokládejme, že jste napsali celé rozdělit funkce. Podle pravidel matematiky dělitel nikdy neměly být nula. Vám může otestovat pomocí kontrolní výraz:  
  
```vb  
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
  
 Při spuštění tohoto kódu v ladicím programu, příkazu kontrolní výraz je vyhodnocen, ale ve vydané verzi není provedeno porovnání, takže není spojena žádná další režie.  
  
 Tady je další příklad. Máte třídu, která implementuje běžný účet následujícím způsobem:  
  
```vb  
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
  
 Před odvolat peníze z účtu, budete chtít zajistěte, aby nepokrývají hodnota, kterou se chystáte odvolat svůj zůstatek na účtu. Můžete například napsat kontrolní výraz ke kontrole zůstatek na účtu:  
  
```vb  
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
  
 Všimněte si, že se volá, aby <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoda zmizí při vytváření verze kódu. To znamená, že volání, která kontroluje zůstatek na účtu zmizí ve vydané verzi. Chcete-li tento problém vyřešit, byste měli vyměnit <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> s <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, který nezmizí ve vydané verzi:  
  
 Volání <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> navýšilo režii vydané verze, na rozdíl od volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a> Vedlejší účinky Debug.Assert –  
 Při použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, ujistěte se, že některý kód uvnitř `Assert` nezmění výsledky program, pokud `Assert` se odebere. V opačném případě může nechtěně způsobit chybu, která se zobrazí jen ve vydané verzi programu. Buďte opatrní hlavně o nepodmíněné výrazy, které obsahují funkce nebo procedury volání, jako v následujícím příkladu:  
  
```vb  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 Toto použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> může se zobrazit bezpečné na první pohled, ale Předpokládejme, že funkce meas aktualizuje čítač pokaždé, když je volána. Při sestavení prodejní verze toto volání meas je Odstraněná, takže čítače neaktualizuje. Toto je příklad funkce s vedlejším účinkem. Odstranění volání funkce, která má vedlejší účinky, může způsobit chybu, která se zobrazí jenom ve vydané verzi. Chcete-li se těmto problémům, neumísťujte volání funkcí v <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> příkazu. Místo toho použijte dočasnou proměnnou:  
  
```vb  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```csharp  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 I při použití <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, můžete chtít stále předejde volání funkce uvnitř `Assert` příkazu. Taková volání by měl být bezpečné, protože <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> nejsou odstraněny příkazů v sestavení pro vydání. Pokud byste se vyhnout tyto konstrukce jak aktualitách, je však méně pravděpodobné, že udělali při použití <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a> Požadavky na ladění a trasování  
 Pokud vytvoříte projekt používá [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] průvodců, symbol trasování je definované ve výchozím nastavení konfigurace vydání a ladění. Ve výchozím nastavení pouze v Laděném sestavení je definován symbol ladění.  
  
 Jinak pro <xref:System.Diagnostics.Trace> metody pro práci, váš program musí mít jeden z následujících akcí v horní části zdrojového souboru:  
  
- `#Const TRACE = True` V jazyce Visual Basic  
  
- `#define TRACE` v jazyce Visual C# a C++  
  
  Nebo program, musí být sestaveny s možností trasování:  
  
- `/d:TRACE=True` V jazyce Visual Basic  
  
- `/d:TRACE` v jazyce Visual C# a C++  
  
  Pokud je potřeba použít metody ladění v jazyce C# nebo Visual Basic verze sestavení, můžete ve vaší konfiguraci vydané verze, definujte symbol ladění.  
  
  Jazyk C++ nepodporuje <xref:System.Diagnostics.Debug> metody třídy. Můžete stejného výsledku dosáhnout pomocí <xref:System.Diagnostics.Trace> třídy s podmíněné kompilace, jako například `#ifdef DEBUG`... `#endif`. Můžete definovat tyto symboly v  **\<Projekt > stránky vlastností** dialogové okno. Další informace najdete v tématu [Změna nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) nebo [Změna nastavení projektu pro konfiguraci ladění jazyka C++ nebo C](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a> Assert – argumenty  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> trvat až tři argumenty. První argument, který je povinný, je podmínky, do kterého chcete zkontrolovat. Při volání <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName> s pouze jedním argumentem `Assert` metoda zkontroluje podmínku a pokud je výsledek false, vypíše obsah zásobník volání a **výstup** okna. Následující příklad ukazuje <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>:  
  
```vb  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 Druhý a třetí argument, pokud jsou k dispozici, musí být řetězce. Při volání <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> nebo <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> dvou nebo tří argumentů je první argument podmínku. Metoda zkontroluje podmínku a pokud je výsledek false, vypíše řetězec druhého a třetího řetězce. Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> a <xref:System.Diagnostics.Trace.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> použita se dvěma argumenty:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 Následující příklad ukazuje <xref:System.Diagnostics.Debug.Assert%2A> a <xref:System.Diagnostics.Trace.Assert%2A>:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```csharp  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a> Přizpůsobení chování Assert  
 Pokud spustíte svou aplikaci v režimu uživatelského rozhraní `Assert` metoda zobrazí **chyba kontrolního výrazu** dialogové okno když podmínky selhání. Akce, které dojde k selhání kontrolní výraz se řídí <xref:System.Diagnostics.Debug.Listeners%2A> nebo <xref:System.Diagnostics.Trace.Listeners%2A> vlastnost.  
  
 Můžete přizpůsobit chování výstup tak, že přidáte <xref:System.Diagnostics.TraceListener> objektu `Listeners` kolekce tak, že odeberete <xref:System.Diagnostics.TraceListener> z `Listeners` kolekce, nebo tak, že přepíšete <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metoda existujícího `TraceListener` k němu chovat jinak.  
  
 Je třeba přepsat <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody zapsat do protokolu událostí místo **chyba kontrolního výrazu** dialogové okno.  
  
 Přizpůsobení výstup tímto způsobem, váš program musí obsahovat naslouchací proces a musí dědit z <xref:System.Diagnostics.TraceListener> a přepsat její <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody.  
  
 Další informace najdete v tématu [naslouchacích procesů trasování](http://msdn.microsoft.com/library/444b0d33-67ea-4c36-9e94-79c50f839025).  
  
 [V tomto tématu](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a> Kontrolní výrazy nastavení v konfiguračních souborech  
 Kontrolní výrazy můžete nastavit v konfiguračním souboru aplikace stejně jako v kódu. Další informace naleznete v tématech <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Trasování a instrumentace aplikací](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Postupy: Podmíněná kompilace pomocí trasování a ladění](http://msdn.microsoft.com/library/56d051c3-012c-42c1-9a58-7270edc624aa)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)



