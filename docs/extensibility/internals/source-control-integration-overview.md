---
title: Přehled integrace správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705114"
---
# <a name="source-control-integration-overview"></a>Přehled integrace správy zdrojového kódu
Tato část porovnává dva způsoby integrace do správy zdrojového kódu sady Visual Studio; modul plug-in správy zdrojového kódu a vspackage, který poskytuje řešení správy zdrojového kódu a zvýrazní nové funkce správy zdrojového kódu. Visual Studio umožňuje ruční přepínání mezi zdrojovým kódem VSPackages a moduly plug-in správy zdrojového kódu, stejně jako automatické přepínání založené na řešení.

## <a name="source-control-integration"></a>Integrace správy zdrojového kódu
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]podporuje dva typy možností integrace správy zdrojového kódu. Ve všech verzích aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]můžete stále integrovat modul plug-in založený na rozhraní PLUG-in správy zdrojového kódu (dříve označované také jako rozhraní API MSSCCI), které poskytuje základní funkce správy zdrojového kódu při použití uživatelského rozhraní správy zdrojového kódu sady Visual Studio. Správa zdrojového kódu VSPackage, na druhé straně poskytuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] novou, hlubokou integrační cestu vhodnou pro integraci správy zdrojového kódu, která vyžaduje vysokou úroveň sofistikovanosti a autonomie v modelu správy zdrojového kódu.

 ![Přehled správy zdrojového kódu](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Modul plug-in správy zdrojového kódu
 Všechny verze sady Visual Studio podporují specifikaci rozhraní API modulu plug-in správy zdrojového kódu verze 1.2 jako cestu integrace. Modul plug-in správy zdrojového kódu zapíše dll, která implementuje funkce rozhraní API modulu plug-in správy zdrojového kódu pro integraci a registraci správy zdrojového kódu, jak je popsáno v [části Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md). V tomto přístupu integrované vývojové prostředí (IDE) používá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské prostředí pro dialogová okna, jako je vrácení se změnami, pokladna, nástroje/možnosti vlastnoststránky stránky, panely nástrojů a glyfy správy zdrojového kódu. Přísné dodržování rozhraní plug-in správy zdrojového kódu zajišťuje snadnou integraci do sady Visual Studio a bezproblémové prostředí pro uživatele. To znamená, že modul plug-in správy zdrojového kódu musí implementovat většinu funkcí a zpětná volání podrobně popsaných v rozhraní API.

 Chcete-li implementovat modul plug-in správy zdrojového kódu pomocí rozhraní API modulu plug-in správy zdrojového kódu, postupujte takto:

1. Vytvořte dll, která implementuje funkce zadané [v modulech plug-in správy zdrojového kódu](../../extensibility/source-control-plug-ins.md).

2. Zaregistrujte dll provedením příslušných položek registru (popsané v [části Postup: Instalace modulu plug-in správy zdrojového kódu).](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. Vytvořte pomocné použití a zobrazení po zobrazení pomocí balíčku adaptéru pro řízení zdrojového kódu (součást sady Visual Studio, která zpracovává funkce správy zdrojového kódu prostřednictvím modulů plug-in správy zdrojového kódu)

   V reakci na příkaz správy zdrojového kódu představuje ide sady Visual Studio standardní rozhraní pro základní operace a poté předá informace modulu plug-in správy zdrojového kódu prostřednictvím funkcí definovaných v rozhraní PLUG-in správy zdrojového kódu. U pokročilých možností může být modul plug-in správy zdrojového kódu volán k prezentaci vlastního uhlavního nastavení, například procházení projektu řízeného zdrojem. To znamená, že uživatel může být zobrazeny s dvěma případně různé styly uživatelského rozhraní při práci s ovládacím prvkem zdrojového kódu: uživatelské rozhraní, které představuje Visual Studio a uživatelské rozhraní, které představuje modul plug-in správy zdrojového kódu. To je nejvíce patrné u pokročilých operací správy zdrojového kódu.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Nevýhody implementace modulu plug-in správy zdrojového kódu

- U pokročilých funkcí může uživatel zobrazit dva různé styly rozhraní, což vede k možnému záměně.

- Modul plug-in správy zdrojového kódu je omezen na model správy zdrojového kódu, který předpokládá rozhraní PLUG-in správy zdrojového kódu.

- Rozhraní plug-in správy zdrojového kódu může být příliš omezující pro některé scénáře správy zdrojového kódu.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Výhody implementace modulu plug-in správy zdrojového kódu

- Visual Studio poskytuje veškeré uzly pro všechny základní operace správy zdrojového kódu tak, aby modul plug-in správy zdrojového kódu není k implementaci potenciálně složité houževnatého řízení.

- Z důvodu striktní rozhraní API modul plug-in správy zdrojového kódu můžete snadno komunikovat s externími programy správy zdrojového kódu poskytovat rozsáhlejší funkce; Visual Studio se příliš nestará o to, jak je funkce správy zdrojového kódu provedena, pouze to, že je provedeno podle rozhraní API modulu plug-in správy zdrojového kódu.

- Je jednodušší implementovat modul plug-in správy zdrojového kódu než zdrojový prvek VSPackage.

## <a name="source-control-vspackage"></a>Správa zdrojového kódu VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Umožňuje hlubokou integraci do sady Visual Studio s úplným řízením funkcí správy zdrojového kódu a úplnou výměnou uživatelského rozhraní správy zdrojového kódu poskytovaného aplikací Visual Studio. Zdrojový ovládací prvek VSPackage je registrován v sadě Visual Studio a poskytuje funkce správy zdrojového kódu. Přestože několik správy zdrojového kódu VSPackages lze zaregistrovat v sadě Visual Studio, pouze jeden z nich může být aktivní v jednom okamžiku. Zdroj ovládacího prvku VSPackage má plnou kontrolu nad funkce správy zdrojového kódu a vzhled v sadě Visual Studio, zatímco je aktivní. Všechny ostatní správy zdrojového kódu VSPackages, které mohou být registrovány v systému jsou neaktivní a nebude zobrazovat žádné ui vůbec.

 Implementace správy zdrojového kódu VSPackage vyžaduje strategii "vše nebo nic". Tvůrce správy zdrojového kódu VSPackage musí investovat značné úsilí do implementace řady rozhraní správy zdrojového kódu a nových prvků uživatelského rozhraní (dialogová okna, nabídky a panely nástrojů) tak, aby pokrývaly celou funkci správy zdrojového kódu. Další podrobnosti najdete [v tématu Vytvoření ovládacího prvku zdrojového kódu VSPackage.](../../extensibility/internals/creating-a-source-control-vspackage.md)

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Nevýhody implementace balíčku VSPackage správy zdrojového kódu

- VSPackage musí implementovat řadu složitých rozhraní úspěšně integrovat s Visual Studio.

- VSPackage musí poskytnout všechny ui potřebné pro správě zdrojového kódu; Visual Studio nebude poskytovat žádnou pomoc v této oblasti.

- Zdrojový ovládací prvek VSPackage je úzce spojena s Visual Studio a nelze pracovat s samostatné programy, takže funkce nelze tak snadno sdílet s externí verzí programu správy zdrojového kódu.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Výhody implementace správy zdrojového kódu VSPackage

- Vzhledem k tomu, že VSPackage má plnou kontrolu nad uživatelskérozhraní správy zdrojového kódu a funkce, uživatel je prezentována s bezproblémové rozhraní pro správě zdrojového kódu.

- VSPackage není omezena na konkrétní model správy zdrojového kódu.

## <a name="see-also"></a>Viz také
- [Správa zdrojového kódu](../../extensibility/internals/source-control.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Co je nového ve správě zdrojového kódu](../../extensibility/internals/what-s-new-in-source-control.md)
