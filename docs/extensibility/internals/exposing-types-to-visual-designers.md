---
title: Vystavení typů vizuálním návrhářům | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708441"
---
# <a name="expose-types-to-visual-designers"></a>Vystavit typy vizuálním návrhářům
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]musí mít přístup k definicím třída a typ v době návrhu, aby bylo možné zobrazit vizuální návrháře. Třídy jsou načteny z předdefinované sady sestavení, které obsahují úplnou sadu závislostí aktuálního projektu (odkazy plus jejich závislosti). Může být také nezbytné pro vizuální návrháři pro přístup třídy a typy, které jsou definovány v souborech generovaných vlastní nástroje.

 A [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektové systémy poskytují podporu pro přístup k generovaným třídám a typům prostřednictvím dočasných přenosných spustitelných souborů (dočasné PEs). Libovolný soubor generovaný vlastním nástrojem lze zkompilovat do dočasnésestavy, takže typy mohou být načteny z těchto sestavení a vystaveny návrhářům. Výstup každého vlastního nástroje je zkompilován do samostatného dočasného PE a úspěch nebo neúspěch této dočasné kompilace závisí pouze na tom, zda lze zkompilovaný soubor zkompilovat. I když projekt nemusí stavět jako celek, jednotlivé dočasné PEs mohou být stále k dispozici návrhářům.

 Systém projektu poskytuje plnou podporu pro sledování změn ve výstupním souboru vlastního nástroje za předpokladu, že tyto změny jsou výsledkem spuštění vlastního nástroje. Při každém spuštění vlastního nástroje je generovánnový dočasný PE a návrhářům jsou odeslána příslušná oznámení.

> [!NOTE]
> Vzhledem k tomu, že dočasný program spustitelný soubor generování se stane na pozadí, žádné chyby jsou hlášeny uživateli, pokud kompilace selže.

 Vlastní nástroje, které využívají dočasnou podporu PE, musí dodržovat následující pravidla:

- **GeneratesDesignTimeSource** musí být v registru nastaveno na 1.

     Bez tohoto nastavení neproběhne žádná kompilace spustitelných souborů programu.

- Generovaný kód musí být ve stejném jazyce jako nastavení globálního projektu.

     Dočasné PE je kompilován bez ohledu na to, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> co vlastní nástroj hlásí jako požadované rozšíření v za předpokladu, že **GeneratesDesignTimeSource** je nastavena na 1 v registru. Rozšíření nemusí být *.vb*, *.cs*nebo *.jsl*; může to být jakékoliv rozšíření.

- Kód generovaný vlastním nástrojem musí být platný a musí zkompilovat samostatně pomocí pouze sady <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> odkazů přítomných v projektu v době dokončení provádění.

     Při zkompilování dočasné PE, pouze zdrojový soubor k dispozici kompilátoru je vlastní výstup nástroje. Proto vlastní nástroj, který používá dočasné PE musí generovat výstupní soubory, které mohou být kompilovány nezávisle na jiných souborů v projektu.

## <a name="see-also"></a>Viz také
- [Úvod k objektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementace jednosouborových generátorů](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrace generátorů s jedním souborem](../../extensibility/internals/registering-single-file-generators.md)
