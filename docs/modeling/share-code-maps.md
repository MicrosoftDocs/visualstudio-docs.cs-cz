---
title: Exportovat a uložit mapy kódu
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267739"
---
# <a name="share-code-maps"></a>Sdílet mapy kódu

Mapy kódu můžete uložit jako součást projektu sady Visual Studio, jako bitovou kopii nebo jako soubor ve formátu XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Mapa kódu sdílet s ostatními uživateli v sadě Visual Studio

Použití **souboru** v nabídce mapy.

-nebo-

Chcete-li uložit mapy v rámci konkrétní projektu, na panelu nástrojů mapy, zvolte **sdílené složky** > **přesunout \<CodeMapName > .dgml do**a pak zvolte projekt, kam chcete uložit Mapa.

![Přesuňte mapu do jiného projektu](../modeling/media/codemapsmovemapmenu.png)

Visual Studio uloží mapy jako *.dgml* souborů, které můžete sdílet s ostatními uživateli aplikace Visual Studio Enterprise a Visual Studio Professional.

> [!NOTE]
> Před sdílením mapu s ty, kteří používají Visual Studio Professional, nezapomeňte rozbalte všechny skupiny, zobrazit skryté uzly a cross-group odkazy a načíst všechny odstraněné uzly, které chcete zobrazit na mapě ostatním uživatelům. Jinak ostatní uživatelé nebudou moci tyto položky zobrazit.
>
> Při uložení mapu, která je v projektu modelování nebo byl zkopírován z projektu modelování do jiného umístění, může dojít k následující chybě:
>
> "Nelze uložit *fileName* mimo adresář projektu. Propojené položky nejsou podporovány.“
>
> Aplikace Visual Studio zobrazí chybu, ale přesto vytvoří uloženou verzi. Aby nedošlo k chybě, vytvoření mapy mimo projekt modelování. Potom jej můžete uložit do požadovaného umístění. Nebude fungovat, pokud budete chtít soubor pouze zkopírovat do jiného umístění v řešení a potom jej uložit.

## <a name="export-a-code-map-as-an-image"></a>Export mapování kódu jako obrázek

Pokud exportujete Mapa kódu jako bitovou kopii, zkopírujte jej do jiných aplikací, jako je například Microsoft Word nebo PowerPoint.

1. Na panelu nástrojů Mapa kódu, zvolte **sdílené složky** > **e-mailu jako obrázek** nebo **Kopírovat obraz**.

2. Vložte obrázek do jiné aplikace.

## <a name="export-the-map-as-an-xps-file"></a>Mapování exportovat jako soubor ve formátu XPS

Pokud exportujete jako soubor ve formátu XPS Mapa kódu, zobrazí se v XML nebo XAML prohlížeče, jako třeba Internet Explorer.

1. Na panelu nástrojů Mapa kódu, zvolte **sdílené složky** > **e-mailu jako přenosné XPS** nebo **uložit jako přenosné XPS**.

2. Kam chcete uložit soubor vyhledejte.

3. Název Mapa kódu. Ujistěte se, že **uložit jako typ** pole je nastavena na **soubory XPS (\*XPS)**. Zvolte **Uložit**.

## <a name="see-also"></a>Viz také

- [Mapování závislostí s mapy kódu](../modeling/map-dependencies-across-your-solutions.md)