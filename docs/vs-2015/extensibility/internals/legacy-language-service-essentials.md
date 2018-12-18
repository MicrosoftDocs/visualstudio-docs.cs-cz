---
title: Základy služby starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c878c4fe124d0443ab5f926a03a378b5b4af014
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753636"
---
# <a name="legacy-language-service-essentials"></a>Základy služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba jazyka pro integraci programovací jazyk do sady Visual Studio je nutné zadat. Toto téma popisuje funkce dostupné ve službě starší verze jazyka services.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace o nový způsob implementace služby jazyka najdete v tématu [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
 Starší verze jazyka služby poskytují následující funkce:  
  
|Funkce|Popis|  
|-------------|-----------------|  
|Barevné zvýrazňování syntaxe|Způsobí, že zobrazení editoru pro zobrazení různé barvy a styly písem definované pro různé prvky jazyka. Toto rozlišení usnadní číst a upravovat soubory.<br /><br /> Obecné informace najdete v tématu [barevné zvýraznění syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci v rámci spravovaného balíčku (MPF) najdete v tématu [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Dokončování příkazů|Dokončení příkazu nebo klíčové slovo, že uživatel začal psát. Doplňování výrazů pomáhají uživatelům snadněji, zadejte obtížné příkazy s kratším a méně pravděpodobnost chyby.<br /><br /> Obecné informace najdete v tématu [dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informace o této funkci ve MPF najdete v tématu [dokončování slov ve službě starší verze jazyka](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Párování závorek|Stručný přehled spárovaná znaky, jako jsou složené závorky. Když uživatel zadá znak pravé, jako "}", párování složených závorek zvýrazní odpovídající počáteční znak, například "{". Když existuje několik úrovní nadřazené znaků, tato funkce pomáhá uživatelům potvrďte, že jsou správně spárované ohraničující znaků.<br /><br /> Informace o této funkci ve MPF najdete v tématu [závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Informace o popisy parametrů|Zobrazí seznam možných podpisy pro přetíženou metodu, která je aktuálně zadání uživatele.<br /><br /> Obecné informace najdete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informace o této funkci ve MPF najdete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Označování chyb|Zobrazí červenou vlnovkou, označované také jako podtržení, v části textu, který je syntakticky nesprávný. Označování chyb se obvykle používají, aby vědět, překlepy v klíčových slovech, neuzavřený závorky, neplatné znaky a podobné chyby uživatele.<br /><br /> Ve třídách MPF označování chyb jsou zpracovány v automaticky <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodu <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy.|  
  
 Mnohé z těchto funkcí vyžadovat služba jazyka analyzovat zdrojový kód. Často můžete opakovaně použít tokenizaci a analýzu kódu pro kompilátor nebo překladač.  
  
 Tyto funkce se vztahují k podpoře programovacích jazyků, ale nejsou součástí jazykových služeb:  
  
|Funkce|Popis|  
|-------------|-----------------|  
|Vyhodnocovače výrazů|Podporuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicí program ověřování zarážek a poskytnutím seznam výrazů, který se má zobrazit v **automatické hodnoty** okno ladění.<br /><br /> Další informace najdete v tématu [podpora služby jazyka pro ladění](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Nástroje procházení symbolů|Podporuje **Prohlížeč objektů**, **zobrazení tříd**, **prohlížeč volání**, a **výsledky hledání symbolu**.|

