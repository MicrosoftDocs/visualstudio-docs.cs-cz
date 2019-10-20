---
title: Kódování a zalomení řádků | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2e1b13cc101ea4d7609633fd9c11bf87946d7b7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665728"
---
# <a name="encodings-and-line-breaks"></a>Šifrování a zalomení řádků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete pomocí nastavení **soubor/rozšířené možnosti uložení** určit typ znaků konce řádku, které chcete. Můžete také změnit kódování souboru se stejným nastavením.

> [!NOTE]
> Pokud máte určité typy nastavení pro vývoj (Visual Basic, F#, vývoj na webu), neuvidíte v nabídce **možnost Upřesnit možnosti ukládání** . Chcete-li změnit nastavení (například obecné), otevřete **nástroje/Import a export nastavení**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 V aplikaci Visual Studio jsou následující znaky interpretovány jako zalomení řádků:

- CRLF: návrat vozík + čára, znaky Unicode 000D + 000A

- LF: line feed, 000A znaků Unicode

- NEL: další řádek, znak Unicode 0085

- LS: oddělovač řádků, znak Unicode 2028

- PS: oddělovač odstavců, znak Unicode 2029

  Text, který je zkopírován z jiných aplikací, uchovává původní kódování a znaky zalomení řádku. Například pokud kopírujete text z programu Poznámkový blok a vložíte ho do textového souboru v aplikaci Visual Studio, text má stejné nastavení jako v poznámkovém bloku.

  Když otevřete soubor, který obsahuje jiné znaky zalomení řádku, může se zobrazit dialogové okno s dotazem, zda by měly být nekonzistentní znaky konců řádků normalizovany a jaký typ konců řádků zvolit.
