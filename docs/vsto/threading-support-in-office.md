---
title: Podpora práce s vlákny v systému Office
description: Dělení na vlákna je podporováno v objektovém modelu systém Microsoft Office. Objektový model Office není bezpečný pro přístup z více vláken, ale může pracovat s více vlákny v řešení Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6fd35551c5c40494c169fb569113e3530f633a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940797"
---
# <a name="threading-support-in-office"></a>Podpora práce s vlákny v systému Office
  Tento článek poskytuje informace o tom, jak je v objektovém modelu systém Microsoft Office podporován dělení na vlákna. Objektový model Office není bezpečný pro přístup z více vláken, ale je možné pracovat s více vlákny v řešení Office. Aplikace Office jsou servery modelu COM (Component Object Model). Model COM umožňuje klientům volat servery COM na libovolných vláknech. U serverů COM, které nejsou vláknově bezpečné, poskytuje model COM mechanizmus pro serializaci souběžných volání, aby se na serveru mohl kdykoli provést pouze jedno logické vlákno. Tento mechanismus je známý jako model STA (Single-threaded Apartment). Vzhledem k tomu, že volání jsou serializována, volající mohou být blokovány po dobu, kdy je server zaneprázdněný nebo zpracovává jiné volání ve vlákně na pozadí.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Požadované znalosti při použití více vláken
 Chcete-li pracovat s více vlákny, musíte mít alespoň základní znalosti následujících aspektů multithreadingu:

- Rozhraní API systému Windows

- Koncepty s více vlákny modelu COM

- Souběžnost

- Synchronizace

- Zařazování

  Obecné informace o multithreading najdete v tématu [spravovaná vlákna](/dotnet/standard/threading/).

  Sada Office běží v hlavním rozhraní STA. Pochopení vlivu tohoto postupu vám umožní pochopit, jak používat více vláken s Office.

## <a name="basic-multithreading-scenario"></a>Základní scénář pro Multithreading
 Kód v řešeních pro systém Office je vždy spuštěn v hlavním vlákně uživatelského rozhraní. Můžete chtít plynule vyhladit výkon aplikace spuštěním samostatné úlohy ve vlákně na pozadí. Cílem je, aby se místo jedné úlohy následovaly dvě úlohy, které následují po druhém, což by mělo vést k plynulejšímu provádění (hlavní důvod pro použití více vláken). Můžete mít například kód události v hlavním vlákně uživatelského rozhraní aplikace Excel a ve vlákně na pozadí můžete spustit úlohu, která shromažďuje data ze serveru a aktualizuje buňky v uživatelském rozhraní aplikace Excel daty ze serveru.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Vlákna na pozadí, která volají do objektového modelu Office
 Když vlákno na pozadí vyvolá volání aplikace sady Office, volání je automaticky zařazeno napříč hranicí STA. Neexistuje však záruka, že aplikace Office může zpracovat volání v době, kdy to vlákno na pozadí udělá. Existuje několik možností:

1. Aplikace Office musí pumpovat zprávy pro volání, aby bylo možné zadat příležitost. Pokud provádí těžké zpracování bez toho, aby to bylo možné, může to chvíli trvat.

2. Pokud je již v objektu Apartment jiný logický podproces, nemůže nové vlákno zadat. K tomu často dochází, když logické vlákno vstoupí do aplikace Office a následně provede zpětné volání zpět do objektu Apartment volajícího. Aplikace zablokovala čekání na vrácení tohoto volání.

3. Excel může být ve stavu, takže nemůže okamžitě zpracovat příchozí volání. Například aplikace Office může zobrazovat modální dialogové okno.

   Pro možnosti 2 a 3 poskytuje model COM rozhraní [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Pokud je server implementuje, všechna volání jsou volána metodou [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . Pro možnost 2 se volání automaticky odmítnou. U možnosti 3 může server odmítnout volání v závislosti na okolnostech. Pokud je volání zamítnuto, volající se musí rozhodnout, co dělat. V normálním případě volající implementuje [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), v takovém případě by se mu v takovém případě oznámilo odmítnutí metodou [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   V případě řešení vytvořených pomocí nástrojů pro vývoj pro Office v sadě Visual Studio však zprostředkovatel komunikace s objekty COM převede všechna zamítnutá volání na <xref:System.Runtime.InteropServices.COMException> ("filtr zpráv indikuje, že aplikace je zaneprázdněná"). Pokaždé, když provedete volání objektového modelu ve vlákně na pozadí, je nutné, abyste mohli zpracovat tuto výjimku. Obvykle to zahrnuje opakování po určitou dobu a pak zobrazení dialogového okna. Můžete ale také vytvořit vlákno na pozadí jako STA a pak pro toto vlákno zaregistrovat filtr zpráv, který tento případ zpracuje.

## <a name="start-the-thread-correctly"></a>Správné spuštění vlákna
 Při vytváření nového vlákna STA nastavte stav bytu na STA předtím, než spustíte vlákno. Následující příklad kódu ukazuje, jak to provést.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Další informace najdete v tématu [osvědčené postupy pro spravované vlákno](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Nemodální formuláře
 Nemodální formulář umožňuje určitý typ interakce s aplikací při zobrazení formuláře. Uživatel komunikuje s formulářem a formulář komunikuje s aplikací bez zavření. Objektový model Office podporuje spravované nemodální formuláře; neměli byste je ale používat ve vlákně na pozadí.

## <a name="see-also"></a>Viz také
- [Dělení na vlákna (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Dělení na vlákna (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Použití vláken a dělení na vlákna](/dotnet/standard/threading/using-threads-and-threading)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
