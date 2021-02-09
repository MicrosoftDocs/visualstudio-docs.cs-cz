---
title: Ladění spravovaného kódu | Microsoft Docs
description: V tématu běžné problémy ladění a techniky v aplikaci Visual Studio pro spravované aplikace nebo aplikace napsané v jazycích, které cílí na modul CLR (Common Language Runtime).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 1cac60b6b7187164780a67be24c7d8bdfb3b4eb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872661"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Ladění spravovaného kódu (C#, Visual Basic, F #, C++/CLI)

Tato část popisuje běžné problémy s laděním a techniky pro spravované aplikace nebo aplikace napsané v jazycích, které cílí na modul CLR (Common Language Runtime), jako je Visual Basic, C# a C++/CLI. Popsané techniky jsou techniky vysoké úrovně. [Nejprve se podíváte na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>V tomto oddílu

[Diagnostické zprávy v okno Výstup](../debugger/diagnostic-messages-in-the-output-window.md)\
Popisuje <xref:System.Diagnostics.Debug> třídy a <xref:System.Diagnostics.Trace> , pomocí kterých lze zapisovat zprávy za běhu do okna **výstup** . Tyto třídy zahrnují výstupní metody, které umožňují výstup informací bez přerušení provádění a výstupu informací, které také přeruší provádění, pokud se konkrétní podmínka nezdařila.

[Kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md)\
Popisuje kontrolní výrazy ve spravovaném kódu, které podmínky testování zadáte jako argumenty `Assert` metod. Kromě toho toto téma poskytuje příklad kódu, informace o použití <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> metodách třídy, informace o ladění a vydání verze kódu, vedlejších důsledcích, argumentech vyhodnocení, přizpůsobení chování kontrolního výrazu a konfiguračních souborech.

[Příkazy stop v Visual Basic](../debugger/stop-statements-in-visual-basic.md)\
Popisuje `Stop` příkaz, který poskytuje alternativu k nastavení zarážky. K dispozici je také příklad kódu, spolu s porovnáním mezi `Stop` příkazem a `End` příkazem a také mezi `Stop` a `Assert` příkazem.

[Návod: ladění formuláře Windows](../debugger/walkthrough-debugging-a-windows-form.md)\
Obsahuje podrobné pokyny pro vytvoření formuláře Windows a ladění tohoto formuláře. Formulář Windows, standardní součást spravované aplikace pro Windows, je jednou z nejběžnějších spravovaných aplikací. Tento návod používá Visual C# a Visual Basic, ale techniky pro vytváření formulářů Windows pomocí C++ jsou obecně podobné.

[Ladění metody OnStart](../debugger/how-to-debug-the-onstart-method.md)\
Poskytuje příklady kódu, které umožňují ladit `OnStart` metodu spravované služby systému Windows. Chcete-li ladit `OnStart` metodu služby systému Windows, je nutné přidat několik řádků kódu pro simulaci služby.

[Ladění ve smíšeném režimu](../debugger/debugging-mixed-mode-applications.md)\
Popisuje ladění aplikací se smíšeným režimem. To znamená, že všechny aplikace, které spojují nativní kód se spravovaným kódem.

[Chyba: ladění není možné, protože v systému je povolen ladicí program jádra.](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
Popisuje chybovou zprávu, která se zobrazí, pokud se pokusíte ladit spravovaný kód v [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] systému,,, [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] nebo Windows NT, který byl spuštěn v režimu ladění.

[Optimalizace a ladění JIT](../debugger/jit-optimization-and-debugging.md)\
Popisuje účinky optimalizace JIT na ladění.

[Ladění LINQ a DLINQ](../debugger/debugging-linq.md)\
Popisuje techniky pro ladění dotazů LINQ.

[Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)\
Popisuje, jak používat okna **paralelních úkolů** a **paralelních zásobníků** k ladění paralelní aplikace.

## <a name="related-sections"></a>Související oddíly

[IntelliTrace](../debugger/intellitrace.md)\
Vyhledávejte chyby rychleji a snadněji a zaznamenáte si historii spuštění vaší aplikace pomocí IntelliTrace. Krokovat zpět a dopředu zaznamenanými událostmi a voláními za účelem prověření stavu vaší aplikace na klíčových místech v čase. Ladění kódu bez nastavování velkého počtu zarážek nebo restartování aplikace, jak často. Vyžaduje Visual Studio Enterprise.

[Trasování a instrumentace aplikací](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Popisuje trasování, způsob, jak můžete monitorovat provádění aplikace, když je spuštěná, a instrumentace, která zahrnuje umístění příkazů Trace ve strategickém umístění v kódu. Toto téma také obsahuje odkazy na Úvod do instrumentace a trasování, přepínače trasování, naslouchací procesy trasování, trasovací kód v aplikaci, přidání příkazů trasování do kódu aplikace a kompilování podmíněně s <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> .

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
Popisuje možnost linkeru, která se přidává <xref:System.Diagnostics.DebuggableAttribute> do kódu napsaného v jazyce C++. Tento atribut je vyžadován pro použití funkcí ladění, jako je například připojení pomocí jazyka C++.

[Ladění aplikací služby systému Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Obsahuje podrobné pokyny pro ladění aplikací služby systému Windows, včetně nastavení, připojení k procesu, ladění kódu v `OnStart` metodě služby a kódu v metodě Main, nastavení zarážek a používání Správce řízení služeb ke spuštění, zastavení, pozastavení a pokračování služby.

[Ladění a profilace](/dotnet/framework/debug-trace-profile/index)\
Popisuje ladění aplikací .NET a požadavků na konfiguraci.

[Ladění skriptů a webových aplikací](how-to-enable-debugging-for-aspnet-applications.md)\
Popisuje běžné problémy s laděním a techniky, se kterými se můžete setkat při ladění skriptů a webových aplikací.

## <a name="see-also"></a>Viz také

- [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)