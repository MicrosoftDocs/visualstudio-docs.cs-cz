---
title: Ladění spravovaného kódu | Microsoft Docs
ms.date: 09/23/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6dd305b55e1ff7dd11b46f023906a8422b5504f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536043"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Ladění spravovaného kóduC#(, Visual Basic F#, C++,/CLI)

Tato část popisuje běžné problémy s laděním a techniky pro spravované aplikace nebo aplikace napsané v jazycích, které cílí na modul CLR (Common Language C#Runtime) C++, jako je Visual Basic, a/CLI. Popsané techniky jsou techniky vysoké úrovně. [Nejprve se podíváte na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>V tomto oddílu

[Diagnostické zprávy v okno Výstup](../debugger/diagnostic-messages-in-the-output-window.md) \
Popisuje třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace>, pomocí kterých lze zapisovat zprávy za běhu do okna **výstup** . Tyto třídy zahrnují výstupní metody, které umožňují výstup informací bez přerušení provádění a výstupu informací, které také přeruší provádění, pokud se konkrétní podmínka nezdařila.

[Kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md) \
Popisuje kontrolní výrazy ve spravovaném kódu, které podmínky testování zadáte jako argumenty `Assert` metody. Kromě toho toto téma poskytuje příklad kódu, informace o použití <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> metod třídy, doporučení v tématu ladění a vydání verze kódu, vedlejších efektů, argumentech vyhodnocení, přizpůsobení chování kontrolního výrazu a konfiguračních souborů.

[Příkazy Stop v Visual Basic](../debugger/stop-statements-in-visual-basic.md) \
Popisuje příkaz `Stop`, který poskytuje alternativu k nastavení zarážky. K dispozici je také příklad kódu společně s porovnáním mezi příkazem `Stop` a příkazem `End` a také mezi `Stop` a příkazem `Assert`.

[Návod: ladění \ formuláře Windows](../debugger/walkthrough-debugging-a-windows-form.md)
Obsahuje podrobné pokyny pro vytvoření formuláře Windows a ladění tohoto formuláře. Formulář Windows, standardní součást spravované aplikace pro Windows, je jednou z nejběžnějších spravovaných aplikací. Tento návod používá vizuál C# a Visual Basic, ale techniky pro vytváření formulářů Windows s C++ jsou všeobecně podobné.

[Ladění metody onstart](../debugger/how-to-debug-the-onstart-method.md) \
Poskytuje příklady kódu, které vám umožní ladit metodu `OnStart` spravované služby systému Windows. Chcete-li ladit metodu `OnStart` služby systému Windows, je nutné přidat několik řádků kódu pro simulaci služby.

[Ladění ve smíšeném režimu](../debugger/debugging-mixed-mode-applications.md) \
Popisuje ladění aplikací se smíšeným režimem. To znamená, že všechny aplikace, které spojují nativní kód se spravovaným kódem.

[Chyba: ladění není možné, protože v systému je povolen ladicí program jádra](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) \
Popisuje chybovou zprávu, která se zobrazí, pokud se pokusíte ladit spravovaný kód v [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] nebo systému Windows NT, který byl spuštěn v režimu ladění.

@No__t_1 [optimalizace a ladění JIT](../debugger/jit-optimization-and-debugging.md)
Popisuje účinky optimalizace JIT na ladění.

[Ladění LINQ a DLINQ](../debugger/debugging-linq.md) \
Popisuje techniky pro ladění dotazů LINQ.

[Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md) \
Popisuje, jak používat okna **paralelních úkolů** a **paralelních zásobníků** k ladění paralelní aplikace.

## <a name="related-sections"></a>Související oddíly

[IntelliTrace](../debugger/intellitrace.md) \
Vyhledávejte chyby rychleji a snadněji a zaznamenáte si historii spuštění vaší aplikace pomocí IntelliTrace. Krokovat zpět a dopředu zaznamenanými událostmi a voláními za účelem prověření stavu vaší aplikace na klíčových místech v čase. Ladění kódu bez nastavování velkého počtu zarážek nebo restartování aplikace, jak často. Vyžaduje Visual Studio Enterprise.

[Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) \
Popisuje trasování, způsob, jak můžete monitorovat provádění aplikace, když je spuštěná, a instrumentace, která zahrnuje umístění příkazů Trace ve strategickém umístění v kódu. Toto téma také obsahuje odkazy na Úvod do instrumentace a trasování, přepínače trasování, naslouchací procesy trasování, trasovací kód v aplikaci, přidání příkazů trasování do kódu aplikace a podmíněné kompilování s <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) \
Popisuje možnost linkeru, která přidá <xref:System.Diagnostics.DebuggableAttribute> do kódu napsaného pomocí C++. Tento atribut je vyžadován pro použití funkcí ladění, jako je například C++připojení k.

[Ladění aplikací služby systému Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) \
Obsahuje pokyny pro ladění aplikací služby systému Windows, včetně nastavení, připojení k procesu, ladění kódu v `OnStart` metody služby a kódu v metodě Main, nastavení zarážek a používání Správce řízení služeb. spuštění, zastavení, pozastavení a pokračování služby.

[Ladění a profilace](/dotnet/framework/debug-trace-profile/index) \
Popisuje ladění aplikací .NET a požadavků na konfiguraci.

[Ladění skriptů a webových aplikací](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) \
Popisuje běžné problémy s laděním a techniky, se kterými se můžete setkat při ladění skriptů a webových aplikací.

## <a name="see-also"></a>Viz také:

- [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)