---
title: Základy starších jazykových služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707427"
---
# <a name="legacy-language-service-essentials"></a>Základy služby starší verze jazyka
Je nutné poskytnout jazykovou službu pro integraci programovacího jazyka do sady Visual Studio. Toto téma vysvětluje funkce dostupné ve službách starších jazyků.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace jazykové služby naleznete v [tématu Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

 Služby starších jazyků poskytují následující funkce:

|Funkce|Popis|
|-------------|-----------------|
|Zbarvení syntaxe|Způsobí, že zobrazení editoru zobrazí různé barvy a styly písma pro různé prvky jazyka. Tato diferenciace může usnadnit čtení a úpravy souborů.<br /><br /> Obecné informace naleznete [v tématu Syntax coloring in a Legacy Language Service](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci v rámci spravovaného balíčku (MPF) naleznete [v tématu Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Dokončení výkazu|Dokončí příkaz nebo klíčové slovo, které uživatel začal psát. Dokončování příkazů pomáhá uživatelům zadávat obtížné příkazy snadněji, s menším počtem psaní a menšími šancemi na chybu.<br /><br /> Obecné informace naleznete [v tématu Dokončení výkazu ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci v MPF naleznete v tématu [Dokončení aplikace Word ve službě starší jazyk](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Shoda složených závorek|Zvýrazní spárované znaky, například závorky. Když uživatel zadá uzavírací znak, například "}", porovnává složená závorka zvýrazní odpovídající počáteční znak, například "{". Pokud existuje několik úrovní ohraničujících znaků, tato funkce pomáhá uživatelům potvrdit, že ohraničující znaky jsou spárovány správně.<br /><br /> Informace o této funkci v MPF naleznete v tématu [Rovnátka odpovídající ve službě starší jazyk](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Popisky informací o parametrech|Zobrazí seznam možných podpisů přetížené metody, kterou uživatel právě zadává.<br /><br /> Obecné informace naleznete [v tématu Informace o parametrech ve službě staršího jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informace o této funkci v MPF naleznete v [tématu Informace o parametrech ve službě staršího jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Značky chyb|Zobrazí podtržení červenou vlnovkou, označované také jako vlnité, pod textem, který je syntakticky nesprávný. Značky chyb se obvykle používají k tomu, aby si uživatelé uvědomili chybně napsaná klíčová slova, neuzavřené závorky, neplatné znaky a podobné chyby.<br /><br /> Ve třídách MPF jsou značky chyb <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> zpracovány <xref:Microsoft.VisualStudio.Package.AuthoringSink> automaticky v metodě třídy.|

 Mnoho z těchto funkcí vyžaduje službu jazyka k analýzě zdrojového kódu. Často můžete znovu použít tokenizační a analyzující kód pro kompilátor nebo interpret.

 Následující funkce souvisejí s podporou programovacích jazyků, ale nejsou součástí jazykových služeb:

| Funkce | Popis |
|-----------------------| - |
| Vyhodnocení výrazů | Podporuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicí program ověřením zarážek a zadáním seznamu výrazů, které mají být zobrazeny v okně ladění **Autos.**<br /><br /> Další informace naleznete v [tématu Podpora jazykových služeb pro ladění](../../extensibility/internals/language-service-support-for-debugging.md). |
| Nástroje pro procházení symbolů | Podporuje **prohlížeč objektů**, zobrazení **tříd**, **prohlížeč volání**a výsledky **hledání symbolů**. |
