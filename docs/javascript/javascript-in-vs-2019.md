---
title: JavaScript a TypeScript v aplikaci Visual Studio 2019
ms.date: 03/27/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 3412e1d27a365a6c6302c56ada865f33a436b639
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888623"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript a TypeScript v aplikaci Visual Studio 2019

## <a name="overview"></a>Přehled

Visual Studio 2019 nabízí bohatou podporu pro vývoj v JavaScriptu, a to jak přímo pomocí JavaScriptu, tak i pomocí [programovacího jazyka TypeScript](http://www.typescriptlang.org/), který byl vyvinutý za účelem zajištění produktivnějšího a užívejte vývoje JavaScriptu. zkušenosti, zejména při vývoji projektů ve velkém měřítku. V aplikaci Visual Studio můžete psát kód JavaScript nebo TypeScript pro mnoho typů aplikací a služeb.

## <a name="javascript-language-service"></a>Služba jazyka JavaScript

Prostředí JavaScript v aplikaci Visual Studio 2019 používá stejný modul, který poskytuje podporu TypeScript. Díky tomu získáte lepší podporu funkcí, bohatou škálu a integraci hned předem.

Možnost obnovení starší verze služby jazyka JavaScript již není k dispozici. Uživatelé teď mají novou službu JavaScript Language Service. Nová jazyková služba je založená výhradně na službě jazyka TypeScript, která využívá statickou analýzu. Díky tomu můžeme poskytovat lepší nástroje, takže váš kód JavaScriptu může využít bohatší technologii IntelliSense na základě definic typů. Nová služba je odlehčená a spotřebovává méně paměti než starší služba, což vám poskytne lepší výkon při škálování kódu. Vylepšili jsme také výkon služby jazyka, aby bylo možné zpracovávat větší projekty.

## <a name="typescript-support"></a>Podpora TypeScript

Visual Studio 2019 poskytuje několik možností pro integraci kompilace TypeScript do vašeho projektu:

* [Balíček NuGet pro TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) Při instalaci balíčku NuGet pro TypeScript 3,2 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.
* TypeScript SDK, který je ve výchozím nastavení dostupný v instalačním programu sady Visual Studio, a také samostatnou sadu SDK stáhnout z [webu vs Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [Balíček TypeScript npm](https://www.npmjs.com/package/typescript) Při instalaci balíčku npm pro TypeScript 2,1 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.

Pro projekty vyvinuté v aplikaci Visual Studio 2019 doporučujeme, abyste používali balíčky TypeScript NuGet a npm pro větší přenositelnost napříč různými platformami a prostředími.

## <a name="projects"></a>Projekty

Javascriptové aplikace UPW se už v sadě Visual Studio 2019 nepodporují. Nemůžete vytvářet ani otevírat projekty UWP v JavaScriptu (soubory s příponou *. JSProj*). Další informace najdete v dokumentaci k [vytváření progresivních Web Apps (PWAs)](/microsoft-edge/progressive-web-apps/get-started) , které se dobře spouštějí v systému Windows.
