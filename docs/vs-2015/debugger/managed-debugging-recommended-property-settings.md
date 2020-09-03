---
title: 'Spravované ladění: doporučené nastavení vlastností | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f63e1382d242a679ed4fac09bfb3040200fed551
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203584"
---
# <a name="managed-debugging-recommended-property-settings"></a>Spravované ladění: doporučené nastavení vlastností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé vlastnosti by měly být nastavené stejným způsobem pro všechny spravované scénáře ladění.  
  
 V následujících tabulkách se zobrazí doporučená nastavení vlastností.  
  
 Nastavení, která tady nejsou uvedená, se můžou lišit v různých spravovaných typech projektů. Například **akce spustit** bude nastavena jinak v projektu model Windows Forms než v [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Vlastnosti konfigurace na kartě Build (C#) nebo Compile (Visual Basic)  
  
|**Název vlastnosti**|**Nastavení**|  
|-----------------------|-----------------|  
|**Definovat konstantu DEBUG**|C# a F #: nastavte zaškrtávací políčko na zaškrtnuto. To umožňuje vaší aplikaci používat třídu ladění.|  
|**Definovat konstantu TRACE**|C# a F #: nastavte zaškrtávací políčko na zaškrtnuto. To umožňuje vaší aplikaci používat třídu Trace.|  
|**Optimalizovat kód**|C#, F # a Visual Basic: nastavte na false. Optimalizovaný kód je těžší ladit, protože vygenerované pokyny neodpovídají přímo vašemu zdrojovému kódu. Pokud zjistíte, že váš program obsahuje chybu, která se zobrazí pouze v optimalizovaném kódu, můžete toto nastavení zapnout, ale mějte na paměti, že kód zobrazený v okně **zpětný překlad** je vygenerován z optimalizovaného zdroje, který se nemusí shodovat s tím, co vidíte v editoru kódu. Chcete-li ladit optimalizovaný kód, je nutné vypnout [pouze můj kód](just-my-code.md).<br /><br /> Další informace naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md) nebo [nastavení projektu pro Visual Basic konfigurace ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Výstupní cesta**|Nastavte na bin\Debug \\ .|  
|**Pokročilé možnosti kompilace**|Pouze Visual Basic. Klikněte na tlačítko **Upřesnit** a nastavte upřesňující vlastnosti, které jsou popsány v následující tabulce.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>dialogové okno Upřesnit nastavení kompilátoru  
  
|**Název vlastnosti**|**Nastavení**|  
|-----------------------|-----------------|  
|**Povolit optimalizace**|Nastavte na hodnotu false z důvodů uvedených v možnosti **optimalizovat kód** v předchozí tabulce.|  
|**Generovat ladicí informace**|Toto políčko zaškrtněte, pokud chcete, aby byl příznak/DEBUG nastaven při kompilaci, který vygeneruje informace potřebné pro usnadnění ladění.|  
|**Definovat konstantu DEBUG**|Toto políčko zaškrtněte, pokud chcete definovat `DEBUG` konstantu, která umožňuje vaší aplikaci používat <xref:System.Diagnostics.Debug> třídu.|  
|**Definovat konstantu TRACE**|Toto políčko zaškrtněte, pokud chcete definovat `TRACE` konstantu, která umožňuje vaší aplikaci používat <xref:System.Diagnostics.Trace> třídu.|  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
