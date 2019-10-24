---
title: Doporučené nastavení vlastností ladicího C#programu, VB | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 07c63a70de9d633ccd73d1d0d3bd23196d421543
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731376"
---
# <a name="managed-debugging-recommended-property-settings"></a>Spravované ladění: doporučené nastavení vlastností
Některé vlastnosti by měly být nastavené stejným způsobem pro všechny spravované scénáře ladění.

 V následujících tabulkách se zobrazí doporučená nastavení vlastností.

 Nastavení, která tady nejsou uvedená, se můžou lišit v různých spravovaných typech projektů. Například **akce spustit** bude nastavena jinak v projektu model Windows Forms než v projektu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Vlastnosti konfigurace na kartě Build (C#) nebo Compile (Visual Basic)

|**Název vlastnosti**|**Nastavením**|
|-----------------------|-----------------|
|**Definovat konstantu DEBUG**|C#a F#: nastavte zaškrtávací políčko na zaškrtnuto. To umožňuje vaší aplikaci používat třídu ladění.|
|**Definovat konstantu TRACE**|C#a F#: nastavte zaškrtávací políčko na zaškrtnuto. To umožňuje vaší aplikaci používat třídu Trace.|
|**Optimalizovat kód**|C#, F#a Visual Basic: nastavte na false. Optimalizovaný kód je těžší ladit, protože vygenerované pokyny neodpovídají přímo vašemu zdrojovému kódu. Pokud zjistíte, že váš program obsahuje chybu, která se zobrazí pouze v optimalizovaném kódu, můžete toto nastavení zapnout, ale mějte na paměti, že kód zobrazený v okně **zpětný překlad** je vygenerován z optimalizovaného zdroje, který se nemusí shodovat s tím, co vidíte v editoru kódu. Chcete-li ladit optimalizovaný kód, je nutné vypnout Pouze můj kód. (Další informace najdete v tématu [Omezení krokování na pouze můj kód](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Další informace naleznete v tématu [nastavení projektu pro C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md) nebo [nastavení projektu pro Visual Basic konfigurace ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Výstupní cesta**|Nastavte na bin\Debug \\.|
|**Pokročilé možnosti kompilace**|Pouze Visual Basic. Klikněte na tlačítko **Upřesnit** a nastavte upřesňující vlastnosti, které jsou popsány v následující tabulce.|

### <a name="advanced-compiler-settings-dialog-box"></a>dialogové okno Upřesnit nastavení kompilátoru

|**Název vlastnosti**|**Nastavením**|
|-----------------------|-----------------|
|**Povolit optimalizace**|Nastavte na hodnotu false z důvodů uvedených v možnosti **optimalizovat kód** v předchozí tabulce.|
|**Generovat ladicí informace**|Toto políčko zaškrtněte, pokud chcete, aby byl příznak/DEBUG nastaven při kompilaci, který vygeneruje informace potřebné pro usnadnění ladění.|
|**Definovat konstantu DEBUG**|Toto políčko zaškrtněte, pokud chcete definovat `DEBUG` konstantu, která umožňuje vaší aplikaci používat třídu <xref:System.Diagnostics.Debug>.|
|**Definovat konstantu TRACE**|Toto políčko zaškrtněte, pokud chcete definovat `TRACE` konstantu, která umožňuje vaší aplikaci používat třídu <xref:System.Diagnostics.Trace>.|

## <a name="see-also"></a>Viz také:
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)