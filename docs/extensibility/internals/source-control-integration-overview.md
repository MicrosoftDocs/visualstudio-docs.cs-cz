---
title: Přehled integrace správy zdrojového kódu | Microsoft Docs
description: 'Přečtěte si o rozdílech mezi dvěma způsoby, jak integrovat správu zdrojového kódu do sady Visual Studio: modul plug-in správy zdrojových kódů a VSPackage.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f3b0ddf956c3f5c2ec2fe51163b52f2a7a973aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846423"
---
# <a name="source-control-integration-overview"></a>Přehled integrace správy zdrojového kódu
Tato část Porovnává dva způsoby, jak integrovat do správy zdrojového kódu sady Visual Studio. Modul plug-in správy zdrojových kódů a VSPackage, který poskytuje řešení správy zdrojového kódu a zvýrazňuje nové funkce správy zdrojového kódu. Visual Studio umožňuje ruční přepínání mezi prvky VSPackage správy zdrojového kódu a moduly plug-in správy zdrojových kódů a také automatickým přepínáním na základě řešení.

## <a name="source-control-integration"></a>Integrace správy zdrojového kódu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje dva typy možností integrace správy zdrojového kódu. Ve všech verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nástroje můžete i nadále integrovat modul plug-in na základě rozhraní API modulu plug-in správy zdrojového kódu (dříve označovaného také jako rozhraní MSSCCI API), které poskytuje základní funkce správy zdrojového kódu při použití uživatelského rozhraní správy zdrojového kódu sady Visual Studio. Sada VSPackage správy zdrojového kódu na druhé straně poskytuje novou, hloubkovou integrační [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] cestu vhodnou pro integraci správy zdrojového kódu, která vyžaduje vysokou úroveň sofistikovanější a autonomii v modelu správy zdrojového kódu.

 ![Přehled správy zdrojového kódu](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Modul plug-in správy zdrojového kódu
 Všechny verze sady Visual Studio podporují specifikaci rozhraní API modulu plug-in správy zdrojového kódu verze 1,2 jako integrační cestu. Modul plug-in správy zdrojových kódů zapisuje knihovnu DLL, která implementuje funkce rozhraní API modulu plug-in správy zdrojového kódu pro integraci a registraci správy zdrojového kódu, jak je popsáno v [tématu Vytvoření modulu plug-in správy](../../extensibility/internals/creating-a-source-control-plug-in.md)zdrojového kódu. V tomto přístupu integrované vývojové prostředí (IDE) používá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské rozhraní pro dialogová okna, jako je vrácení se změnami, rezervace, nástroje/Možnosti stránky vlastností, panely nástrojů a glyfy správy zdrojového kódu. Striktní dodržování rozhraní API pro modul plug-in správy zdrojových kódů zajišťuje jednoduchou integraci do sady Visual Studio a možnosti bezplatného řešení pro uživatele v bezproblémovém prostředí. To znamená, že modul plug-in správy zdrojových kódů musí implementovat většinu funkcí a zpětných volání, která jsou popsána v rozhraní API.

 Chcete-li implementovat modul plug-in správy zdrojových kódů pomocí rozhraní API modulu plug-in správy zdrojového kódu, postupujte následovně:

1. Vytvořte knihovnu DLL, která implementuje funkce určené v [modulu plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md).

2. Zaregistrujte knihovnu DLL tak, že provedete příslušné položky registru (popsané v tématu [Postupy: Instalace modulu plug-in správy zdrojových kódů](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Vytvoření uživatelského rozhraní pomocníka a zobrazení po zobrazení výzvy balíčkem adaptéru správy zdrojového kódu (součást sady Visual Studio, která zpracovává funkce správy zdrojového kódu přes moduly plug-in správy zdrojového kódu)

   V reakci na příkaz správy zdrojového kódu integrované vývojové prostředí (IDE) sady Visual Studio prezentuje standardní uživatelské rozhraní pro základní operace a pak předá informace do modulu plug-in správy zdrojových kódů prostřednictvím funkcí definovaných v rozhraní API modulu plug-in správy zdrojového kódu. V případě pokročilých možností může být modul plug-in správy zdrojových kódů volán pro vlastní uživatelské rozhraní, například procházení pro projekt se spravovanými zdroji. To znamená, že uživatel může být při práci se správou zdrojových kódů zobrazen se dvěma případně různými styly uživatelského rozhraní: uživatelské rozhraní, které Visual Studio prezentuje, a uživatelské rozhraní, které modul plug-in správy zdrojových kódů prezentuje. To je nejužitečnější s pokročilými operacemi správy zdrojových kódů.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nevýhody implementace modulu plug-in správy zdrojových kódů

- V případě pokročilých funkcí může uživatel vidět dva různé styly rozhraní, což může vést k nejasnostem.

- Modul plug-in správy zdrojových kódů je omezen na model správy zdrojového kódu odvozený rozhraním API modulu plug-in správy zdrojového kódu.

- Rozhraní API modulu plug-in správy zdrojového kódu může být pro některé scénáře správy zdrojových kódů příliš omezující.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Výhody implementace modulu plug-in správy zdrojového kódu

- Visual Studio poskytuje všechna rozhraní pro všechny základní operace správy zdrojových kódů, aby modul plug-in správy zdrojových kódů nemusel implementovat potenciálně komplexní uživatelské rozhraní.

- Z důvodu striktního rozhraní API může modul plug-in správy zdrojových kódů snadno komunikovat s externími programy pro správu zdrojového kódu, aby poskytoval širší funkčnost. Visual Studio nezáleží na tom, jak se provádí funkce správy zdrojového kódu, a to pouze v souladu s rozhraním API modulu plug-in správy zdrojového kódu.

- Je snazší implementovat modul plug-in správy zdrojového kódu, než je VSPackage správy zdrojového kódu.

## <a name="source-control-vspackage"></a>VSPackage správy zdrojového kódu
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] umožňuje hloubkovou integraci do sady Visual Studio s plnou kontrolou funkcí správy zdrojového kódu a kompletní nahrazení sady Visual Studio, které poskytuje uživatelské rozhraní správy zdrojového kódu. Balíček VSPackage správy zdrojového kódu je zaregistrován v aplikaci Visual Studio a poskytuje funkce správy zdrojového kódu. I když se sadou Visual Studio dá zaregistrovat několik VSPackage správy zdrojového kódu, může být v jednom okamžiku aktivní jenom jeden z nich. VSPackage správy zdrojového kódu má plnou kontrolu nad funkcemi a vzhled správy zdrojového kódu v aplikaci Visual Studio, když je aktivní. Všechny ostatní sady VSPackage správy zdrojového kódu, které mohou být zaregistrované v systému, jsou neaktivní a nezobrazí se žádné uživatelské rozhraní.

 Implementace balíčku VSPackage správy zdrojového kódu vyžaduje strategii "vše nebo Nothing". Tvůrce balíčku VSPackage pro správu zdrojového kódu musí investovat značnou náročnost při implementaci řady rozhraní správy zdrojového kódu a nových prvků uživatelského rozhraní (dialogová okna, nabídky a panely nástrojů), aby pokryly celou funkci správy zdrojového kódu. Další podrobnosti najdete v tématu [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md) .

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nevýhody implementace balíčku VSPackage správy zdrojového kódu

- VSPackage musí implementovat řadu složitých rozhraní pro úspěšnou integraci se sadou Visual Studio.

- VSPackage musí poskytovat veškeré uživatelské rozhraní požadované pro správu zdrojového kódu; Visual Studio nebude v této oblasti poskytovat žádnou pomoc.

- Prvek VSPackage správy zdrojového kódu je podrobnějším pohledu zjistíte svázaný se sadou Visual Studio a nemůže pracovat se samostatnými programy, takže funkčnost nemůže být stejně snadné sdílet s externí verzí programu správy zdrojového kódu.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Výhody implementace balíčku VSPackage správy zdrojového kódu

- Protože VSPackage má úplnou kontrolu nad uživatelským rozhraním a funkcemi správy zdrojových kódů, zobrazí se uživateli bezproblémové rozhraní pro správu zdrojového kódu.

- VSPackage není omezen na konkrétní model správy zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Správa zdrojového kódu](../../extensibility/internals/source-control.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Co je nového ve správě zdrojového kódu](../../extensibility/internals/what-s-new-in-source-control.md)
