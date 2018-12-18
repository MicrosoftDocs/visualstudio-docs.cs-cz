---
title: Podpora v systému Office práce s vlákny
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aafdad425d611d7d57c2ae8e53e505d3522ba38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871105"
---
# <a name="threading-support-in-office"></a>Podpora v systému Office práce s vlákny
  Tento článek obsahuje informace o způsobu práce s vlákny je podporována v objektovém modelu aplikace Microsoft Office. Objektový model Office není bezpečné pro vlákna, ale je možné pracovat s více vlákny v řešení pro Office. Aplikace Office jsou serverů modelu COM (Component Object). COM umožňuje klientům volání serverů modelu COM na libovolného vlákna. U serverů modelu COM, které nejsou bezpečné pro vlákna COM poskytuje mechanismus pro serializaci souběžných volání tak, aby pouze jeden logické vlákno spustí na serveru kdykoli. Tento mechanismus je označován jako jednovláknový objekt apartment (STA) modelu. Protože volání jsou serializovaná, může být blokovaný volající časová období, zatímco server je zaneprázdněn nebo je zpracování jiných volání na vlákně na pozadí.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Požaduje se při použití více vláken znalostní báze  
 Pro práci s více vlákny, musí mít aspoň základní znalosti o následující aspekty multithreading:  
  
- Rozhraní Windows API  
  
- COM s více vlákny koncepty  
  
- Souběžnost  
  
- Synchronizace  
  
- zařazování  
  
  Obecné informace o multithreading, viz [dělení na spravovaná vlákna](/dotnet/standard/threading/).  
  
  Office běží v hlavní STA. Vysvětlení důsledků to umožňuje porozumět způsobu použití více vláken s Office.  
  
## <a name="basic-multithreading-scenario"></a>Základní scénář pro multithreading  
 Kód v řešeních pro systém Office je vždy spuštěn na hlavním vlákně uživatelského rozhraní. Můžete chtít vyhlazení výkonu aplikace spuštěním samostatné úlohy na vlákně na pozadí. Cílem je provést dvě úlohy zdánlivě najednou místo jeden úkol, za nímž následuje druhé, což by měl mít za následek hladší spuštění (hlavní důvod pro použití více vláken). Například může mít kód událostí na hlavním vlákně uživatelského rozhraní aplikace Excel a na vlákně na pozadí může spustit úlohu, která shromažďuje data ze serveru a aktualizuje buněk v Uživatelském rozhraní aplikace Excel s daty ze serveru.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Vláken na pozadí, které volají do modelem objektů sady Office  
 Když vlákno na pozadí aplikace Office zavolá, volání je Zařazováno automaticky přes hranice STA. Však neexistuje žádná záruka, že aplikace Office dokáže zpracovat volání v době, že umožňuje vlákna na pozadí. Existuje několik možností:  
  
1. Aplikace Office musí pumpa zpráv pro volání příležitost k zadání. Pokud je to náročná na výkon zpracování bez získávání to může trvat.  
  
2. Pokud jiné logické vlákno už je v typu apartment, nelze zadat nové vlákno. Často se to stane, když logické vlákno přejde do aplikace sady Office a potom je vícenásobné volání zpět do volajícího objektu apartment. Aplikace se zablokuje čekáním toto volání se vraťte.  
  
3. Excel může být ve stavu, takže nemůže zpracovat okamžitě příchozí volání. Například aplikace Office může být zobrazení modální dialogové okno.  
  
   Poskytuje možnosti 2 a 3, COM [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) rozhraní. Pokud jej implementuje na server, zadejte všechna volání prostřednictvím [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) metody. Možnost 2 jsou automaticky zamítnuty volání. Možnost 3 server může zamítnout volání, v závislosti na okolnostech. Pokud je volání, volající musíte rozhodnout, jak postupovat. Za normálních okolností implementuje volající [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), v takovém případě by informováni o zamítnutí podle [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) metody.  
  
   Ale v případě řešení vytvořená pomocí nástroje pro vývoj pro Office v sadě Visual Studio, komunikace s objekty COM převede všechny odmítnuté volání <xref:System.Runtime.InteropServices.COMException> ("filtr zpráv uvedeno, že aplikace je zaneprázdněna"). Vždy, když provedete objektový model volání na vlákně na pozadí, musí být připravena zpracovat tuto výjimku. Obvykle budete muset opakování pro určité množství času a pak zobrazení dialogového okna. Můžete však také vytvořit vlákno na pozadí jako STA a pak zaregistrujte filtru zpráv pro toto vlákno zpracovat tento případ.  
  
## <a name="start-the-thread-correctly"></a>Spuštění vlákna  
 Při vytváření nového vlákna STA nastavte stav objektu apartment STA před spuštěním podprocesu. Následující příklad kódu ukazuje, jak to provést.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Další informace najdete v tématu [dělení na spravovaná vlákna osvědčené postupy](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Nemodální formuláře  
 Nemodální formuláře umožňuje nějaký typ interakce s aplikací, zatímco se zobrazí formulář. Uživatel pracuje s formuláři a formuláři komunikuje s aplikací bez zavření. Objektový model Office podporuje spravované nemodální formuláře; je ale by neměly používat podle vlákna na pozadí.  
  
## <a name="see-also"></a>Viz také:  
 [Dělení na spravovaná vlákna](/dotnet/standard/threading/)  
 [Dělení na vlákna (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [dělení na vlákna (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Použití vláken a dělení na vlákna](/dotnet/standard/threading/using-threads-and-threading)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)  
  
  