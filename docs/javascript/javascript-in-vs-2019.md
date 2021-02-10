---
title: JavaScript a TypeScript v aplikaci Visual Studio 2019
description: Přečtěte si, jak Visual Studio 2019 poskytuje bohatou podporu pro vývoj v JavaScriptu, jak přímo pomocí JavaScriptu, tak i pomocí programovacího jazyka TypeScript.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0fe13030478f62f759b3eabc8e897c09a4295bad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936753"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript a TypeScript v aplikaci Visual Studio 2019

## <a name="overview"></a>Přehled

Visual Studio 2019 nabízí bohatou podporu pro vývoj v JavaScriptu, a to jak přímo pomocí JavaScriptu, tak i pomocí [programovacího jazyka TypeScript](http://www.typescriptlang.org/), který byl vyvinutý za účelem zajištění výkonnějšího a užívejte prostředí pro vývoj JavaScriptu, zejména při vývoji projektů ve velkém měřítku. V aplikaci Visual Studio můžete psát kód JavaScript nebo TypeScript pro mnoho typů aplikací a služeb.

## <a name="javascript-language-service"></a>Služba jazyka JavaScript

Prostředí JavaScript v aplikaci Visual Studio 2019 používá stejný modul, který poskytuje podporu TypeScript. Díky tomu získáte lepší podporu funkcí, bohatou škálu a integraci hned předem.

Možnost obnovení starší verze služby jazyka JavaScript již není k dispozici. Uživatelé teď mají novou službu JavaScript Language Service. Nová jazyková služba je založená výhradně na službě jazyka TypeScript, která využívá statickou analýzu. Díky tomu můžeme poskytovat lepší nástroje, takže váš kód JavaScriptu může využít bohatší technologii IntelliSense na základě definic typů. Nová služba je odlehčená a spotřebovává méně paměti než starší služba, což vám poskytne lepší výkon při škálování kódu. Vylepšili jsme také výkon služby jazyka, aby bylo možné zpracovávat větší projekty.

## <a name="typescript-support"></a>Podpora TypeScript

Visual Studio 2019 poskytuje několik možností pro integraci kompilace TypeScript do vašeho projektu:

* [Balíček NuGet pro TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) Při instalaci balíčku NuGet pro TypeScript 3,2 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.
* [Balíček TypeScript npm](https://www.npmjs.com/package/typescript) Při instalaci balíčku npm pro TypeScript 2,1 nebo vyšší do projektu se v editoru načte odpovídající verze jazykové služby TypeScript.
* TypeScript SDK, který je ve výchozím nastavení dostupný v instalačním programu sady Visual Studio, a také samostatnou sadu SDK stáhnout z [webu vs Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395).

> [!TIP]
> Pro projekty vyvinuté v aplikaci Visual Studio 2019 doporučujeme, abyste pro větší přenositelnost napříč různými platformami a prostředími používali NuGet NuGet nebo balíček TypeScript npm. Další informace najdete v tématu [kompilování kódu TypeScript pomocí NuGet](../javascript/compile-typescript-code-nuget.md) a [kompilování kódu TypeScript pomocí čítače TSC](../javascript/compile-typescript-code-npm.md).

## <a name="projects"></a>Projekty

Javascriptové aplikace UPW se už v sadě Visual Studio 2019 nepodporují. Nemůžete vytvářet ani otevírat projekty UWP v JavaScriptu (soubory s příponou *. JSProj*). Další informace najdete v dokumentaci k [vytváření progresivních Web Apps (PWAs)](/microsoft-edge/progressive-web-apps/get-started) , které se dobře spouštějí v systému Windows.
