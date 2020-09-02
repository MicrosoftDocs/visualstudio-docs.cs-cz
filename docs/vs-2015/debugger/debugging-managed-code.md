---
title: Ladění spravovaného kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39076459f684aafce4e800ecad6341d120aac480
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691450"
---
# <a name="debugging-managed-code"></a>Ladění spravovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část popisuje běžné problémy s laděním a techniky pro spravované aplikace nebo aplikace napsané v jazycích, které cílí na modul CLR (Common Language Runtime), jako jsou Visual Basic, C# a C++. Popsané techniky jsou techniky vysoké úrovně. Další informace naleznete v tématu [použití ladicího programu](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Diagnostické zprávy v okně Výstup](../debugger/diagnostic-messages-in-the-output-window.md)  
 Popisuje <xref:System.Diagnostics.Debug> třídy a <xref:System.Diagnostics.Trace> , pomocí kterých lze zapisovat zprávy za běhu do okna **výstup** . Tyto třídy zahrnují výstupní metody, které umožňují výstup informací bez přerušení provádění a výstupu informací, které také přeruší provádění, pokud se konkrétní podmínka nezdařila.  
  
 [Kontrolní výrazy ve spravovaném kódu](../debugger/assertions-in-managed-code.md)  
 Popisuje kontrolní výrazy ve spravovaném kódu, které podmínky testování zadáte jako argumenty `Assert` metod. Kromě toho toto téma poskytuje příklad kódu, informace o použití <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> metodách třídy, informace o ladění a vydání verze kódu, vedlejších důsledcích, argumentech vyhodnocení, přizpůsobení chování kontrolního výrazu a konfiguračních souborech.  
  
 [Příkazy Stop v jazyce Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Popisuje `Stop` příkaz, který poskytuje alternativu k nastavení zarážky. K dispozici je také příklad kódu, spolu s porovnáním mezi `Stop` příkazem a `End` příkazem a také mezi `Stop` a `Assert` příkazem.  
  
 [Návod: Ladění formuláře systému Windows](../debugger/walkthrough-debugging-a-windows-form.md)  
 Obsahuje podrobné pokyny pro vytvoření formuláře Windows a ladění tohoto formuláře. Formulář Windows, standardní součást spravované aplikace pro Windows, je jednou z nejběžnějších spravovaných aplikací. Tento návod používá Visual C# a Visual Basic, ale techniky pro vytváření formulářů Windows pomocí C++ jsou obecně podobné.  
  
 [Ladění metody OnStart](../debugger/how-to-debug-the-onstart-method.md)  
 Poskytuje příklady kódu, které umožňují ladit `OnStart` metodu spravované služby systému Windows. Chcete-li ladit `OnStart` metodu služby systému Windows, je nutné přidat několik řádků kódu pro simulaci služby.  
  
 [Ladění ve smíšeném režimu](../debugger/debugging-mixed-mode-applications.md)  
 Popisuje ladění aplikací se smíšeným režimem. To znamená, že všechny aplikace, které spojují nativní kód se spravovaným kódem.  
  
 [Chyba: Ladění není možné, protože v systému je povolen ladicí program protokolu Kernel.](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Popisuje chybovou zprávu, která se zobrazí, pokud se pokusíte ladit spravovaný kód v [!INCLUDE[win7](../includes/win7-md.md)] [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] systému,,, [!INCLUDE[winxp](../includes/winxp-md.md)] [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)] nebo Windows NT, který byl spuštěn v režimu ladění.  
  
 [Optimalizace a ladění JIT](../debugger/jit-optimization-and-debugging.md)  
 Popisuje účinky optimalizace JIT na ladění.  
  
 [Ladění LINQ a DLINQ](../debugger/debugging-linq.md)  
 Popisuje techniky pro ladění dotazů LINQ.  
  
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Popisuje, jak používat okna **paralelních úkolů** a **paralelních zásobníků** k ladění paralelní aplikace.  
  
## <a name="related-sections"></a>Související oddíly  
 [IntelliTrace](../debugger/intellitrace.md)  
 Vyhledávejte chyby rychleji a snadněji a zaznamenáte si historii spuštění vaší aplikace pomocí IntelliTrace. Krokovat zpět a dopředu zaznamenanými událostmi a voláními za účelem prověření stavu vaší aplikace na klíčových místech v čase. Ladění kódu bez nastavování velkého počtu zarážek nebo restartování aplikace, jak často. Vyžaduje Visual Studio Ultimate.  
  
 [Trasování a instrumentace aplikací](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 Popisuje trasování, způsob, jak můžete monitorovat provádění aplikace, když je spuštěná, a instrumentace, která zahrnuje umístění příkazů Trace ve strategickém umístění v kódu. Toto téma také obsahuje odkazy na Úvod do instrumentace a trasování, přepínače trasování, naslouchací procesy trasování, trasovací kód v aplikaci, přidání příkazů trasování do kódu aplikace a kompilování podmíněně s <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> .  
  
 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 Popisuje možnost linkeru, která se přidává <xref:System.Diagnostics.DebuggableAttribute> do kódu napsaného v jazyce C++. Tento atribut je vyžadován pro použití funkcí ladění, jako je například připojení pomocí jazyka C++.  
  
 [Ladění aplikací služby systému Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Obsahuje podrobné pokyny pro ladění aplikací služby systému Windows, včetně nastavení, připojení k procesu, ladění kódu v `OnStart` metodě služby a kódu v metodě Main, nastavení zarážek a používání Správce řízení služeb ke spuštění, zastavení, pozastavení a pokračování služby.  
  
 [Ladění a profilace](https://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 Popisuje ladění aplikací .NET Framework a požadavků na konfiguraci.  
  
 [Ladění skriptů a webových aplikací](../debugger/debugging-web-applications-and-script.md)  
 Popisuje běžné problémy s laděním a techniky, se kterými se můžete setkat při ladění skriptů a webových aplikací.  
 Popis nových funkcí ladění přidaných v této verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Domovská stránka ladění](../debugger/debugging-in-visual-studio.md)  
 Obsahuje odkazy na větší části dokumentace ladění. Informace zahrnují novinky v ladicím programu, nastavení a přípravu, zarážky, zpracování výjimek, úpravy a pokračování, ladění spravovaného kódu, ladění Visual C++ projektů, ladění modelu COM a ActiveX, ladění knihoven DLL, ladění SQL a odkazy na uživatelské rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](https://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
