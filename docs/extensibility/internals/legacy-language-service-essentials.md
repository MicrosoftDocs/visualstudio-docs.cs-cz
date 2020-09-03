---
title: Základy služby starší verze jazyka | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707427"
---
# <a name="legacy-language-service-essentials"></a>Základy služby starší verze jazyka
Je nutné zadat jazykovou službu pro integraci programovacího jazyka do sady Visual Studio. V tomto tématu najdete vysvětlení funkcí dostupných ve starších jazykových službách.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace jazykové služby najdete v tématu [rozšíření pro Editor a jazykové služby](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

 Starší jazykové služby poskytují následující funkce:

|Funkce|Popis|
|-------------|-----------------|
|Barevné zvýrazňování syntaxe|Způsobí, že zobrazení editoru zobrazí různé barvy a styly písma pro různé prvky jazyka. Tato odlišnost usnadňuje čtení a úpravy souborů.<br /><br /> Obecné informace najdete v tématu [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci v rozhraní Managed Package Framework (MPF) najdete v tématu [syntaxe Colorizing ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Dokončování příkazů|Dokončí příkaz nebo klíčové slovo, které uživatel zahájil při psaní. Dokončování příkazů pomáhá uživatelům rychleji zadávat obtížné příkazy s menším počtem zadání a menší pravděpodobností chyby.<br /><br /> Obecné informace najdete v tématu [dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci v poli MPF najdete v tématu [dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Spárování složených závorek|Zvýrazní spárované znaky, jako jsou složené závorky. Když uživatel zadá uzavírací znak, například "}", při shodě složených závorek se zvýrazní odpovídající znak pro otevření, například "{". V případě, že existuje několik úrovní ohraničujících znaků, tato funkce pomůže uživatelům zkontrolovat, zda jsou ohraničující znaky spárovány správně.<br /><br /> Informace o této funkci v poli MPF najdete v tématu [porovnání složených závorek ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Popisy informací o parametrech|Zobrazí seznam možných signatur pro přetíženou metodu, kterou uživatel právě zapisuje.<br /><br /> Obecné informace najdete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informace o této funkci v souboru MPF naleznete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Chybové značky|Zobrazí červené podtržení vlnovkou, označované také jako vlnovka, v části text, který není syntakticky správný. Chybové značky obvykle slouží k tomu, aby uživatelé věděli o nesprávně napsaných klíčových slovech, neuzavřených závorkách, neplatných znacích a podobných chybách.<br /><br /> V třídách MPF jsou chybové značky zpracovávány automaticky v <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodě <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy.|

 Mnohé z těchto funkcí vyžadují, aby služba jazyka analyzovala zdrojový kód. Často můžete znovu použít tokenizací a analyzovat kód pro kompilátor nebo interpret.

 Následující funkce souvisejí s podporou programovacích jazyků, ale nejsou součástí jazykových služeb:

| Funkce | Popis |
|-----------------------| - |
| Vyhodnocovací filtry výrazů | Podporuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicí program pomocí ověřování zarážek a zadání seznamu výrazů, které se mají zobrazit v okně **Automatické** ladění.<br /><br /> Další informace najdete v tématu [Podpora jazykové služby pro ladění](../../extensibility/internals/language-service-support-for-debugging.md). |
| Nástroje pro procházení symbolů | Podporuje **Prohlížeč objektů**, **zobrazení tříd**, **prohlížeč volání**a **výsledky hledání symbolů**. |
