---
title: Novinky pro programátory v sadě Visual Studio 2017
description: Seznamte se s novými funkcemi pro návrh kódu, jako je ověřování živé závislosti, které jsou k dispozici v aplikaci Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 00a72f52b67e1e55bcc0699a3daf7da4dcfbc57d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924009"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novinky pro programátory v sadě Visual Studio 2017

## <a name="live-dependency-validation"></a>Ověřování závislostí v reálném čase

Odebrání nežádoucích závislostí je důležitou součástí správy technického dluhu. Visual Studio poskytuje živé ověření závislostí, včetně podrobných informací o problémech, například místa, kde se nacházejí. Ověřování závislostí v reálném čase má plné výhody pro nové funkce Seznam chyb a editoru.

![Ověřování závislostí v akci v reálném čase](media/dep-validation-whatsnew-01.png)

Prostředí pro vytváření obsahu se změnilo tak, aby ověřování závislostí bylo více Zjistitelnější a bylo dostupné. Terminologie se změnila z "diagramu vrstev" na "Diagram závislostí".

Nabídka **Architektura** teď obsahuje příkaz pro přímé vytvoření diagramu závislostí:

![Živá položka závislosti v nabídce architektury](media/dep-validation-whatsnew-02.png)

Názvy vlastností vrstvy a popisy byly změněny, aby byly smysluplnější:

![Názvy vlastností aktualizovaných závislostí za provozu](media/dep-validation-whatsnew-03.png)

Okamžitě uvidíte dopad změn ve výsledcích analýzy pro aktuální kód v řešení pokaždé, když diagram uložíte. Nemusíte čekat na dokončení příkazu **ověřit závislosti** .

Další podrobnosti najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Návrháři UML se odebraly

Návrháři UML byly ze sady Visual Studio odebrány.

* Diagramy UML se teď prezentují jako soubory XML.
* Průzkumník modelů UML už neexistuje.
* Odkazy na projekt modelování se již nepoužívají pro ověřování závislostí.
* Uzel odkazy na vrstvu v Průzkumník řešení se už nezobrazuje.
* Akce "ověřit" sestavení v diagramu závislosti (vrstvy) se už nepoužívá – úloha sestavení se odebrala.
* Struktura projektu je udržována pro kulaté Trip mezi verzemi.
* Můžete přesto otevřít, vytvořit, upravit a uložit závislost (diagram vrstev) jako XML.
* Pracovní položky sady TFS propojené s diagramem závislosti (vrstvy) nejsou pro návrhovou plochu dostupné.
* Zpětná propojení z na DSL nebo vrstvu už není podporovaná.
* Rozšiřitelnost UML v sadě Modeling SDK už není podporovaná.

Podpora pro vizualizaci architektury kódu .NET a C++ je k dispozici prostřednictvím [map kódu](map-dependencies-across-your-solutions.md).

Pokud se jedná o významného uživatele návrháře UML, můžete i nadále používat sadu Visual Studio 2015 nebo starší verze a současně se rozhodnout o alternativním nástroji pro potřeby UML.

Další podrobnosti najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edice pro nástroje pro architekturu a modelování

Visual Studio je k dispozici v několika edicích. Ne všechny tyto možnosti poskytují podporu pro architektury a nástroje pro modelování. V následující tabulce je uveden seznam dostupnosti jednotlivých nástrojů.

|**Funkce**|**Edice Enterprise**|**Professional Edition**|**Edice Community**|
|-|-|-|-|
|**Mapy kódu**|Ano|Podporuje pouze čtení map kódu, filtrování map kódu, přidávání nových obecných uzlů a vytvoření nového orientovaného grafu z výběru.|-|
|**Diagramy závislostí**|Ano|Podporuje pouze čtení diagramů závislostí.|Podporuje pouze čtení diagramů závislostí.|
|**Orientované grafy** (diagramy DGML)|Ano|Ano|Ano|
|**Klon kódu**|Ano|-|-|
