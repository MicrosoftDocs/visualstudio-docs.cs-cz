---
title: Úlohy ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200614"
---
# <a name="debugging-tasks"></a>Úlohy ladění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chcete-li ladit program, musí být spuštěn a k němu musí být připojen ladicí stroj (DE), nebo jinak musí být k dříve spuštěnému programu připojen příkaz DE. Po připojení musí DE vygenerovat určité události spuštění. V reakci se ladicí balíček pokusí vázat zarážky nastavené v integrovaném vývojovém prostředí (IDE). Když program narazí na vázanou zarážku, zastaví a počká na vstup uživatele.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Problémy se zabezpečením](../../extensibility/debugger/security-issues.md)  
 Popisuje kroky zabezpečení, které jsou nutné k ladění programu.  
  
 [Spuštění programu](../../extensibility/debugger/launching-a-program.md)  
 Poskytuje podrobné pokyny, jak zadat DE, který volá operační systém pro spuštění programu.  
  
 [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Popisuje proces, který se používá k ladění programu v procesu, který je už spuštěný.  
  
 [Odesílání událostí spuštění po spuštění](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Zobrazuje události, které se provádějí po připojení DE k programu, dokud je program v jeho hlavním vstupním bodě a připravený k ladění.  
  
 [Řízení spouštění](../../extensibility/debugger/control-of-execution.md)  
 Vysvětluje, jak obvykle pošle událost vstupního bodu, událost dokončení načtení nebo událost zastavení v závislosti na okolnostech.  
  
 [Vytváření vazeb zarážek](../../extensibility/debugger/binding-breakpoints.md)  
 Popisuje, jak, pokud uživatel nastaví zarážku, rozhraní IDE formuluje požadavek a vyzve relaci ladění, aby vytvořila zarážku.  
  
 [Vyhodnocování výrazů](../../extensibility/debugger/evaluating-expressions.md)  
 Vysvětluje, jak se vytvářejí výrazy a co se stane, když se vyhodnotí výraz.  
  
 [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Vysvětluje, jakým způsobem vyhodnocovací filtr výrazů (EE) podporuje typy vizualizace a vlastní prohlížeče.  
  
## <a name="related-sections"></a>Související oddíly  
 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)  
 Popisuje hlavní koncepty architektury ladění.  
  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)  
 Poskytuje přehled komponent ladění sady Visual Studio, které zahrnují popisovač DE, EE a symbol (SH).  
  
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md)  
 Vysvětluje, jak DE funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
