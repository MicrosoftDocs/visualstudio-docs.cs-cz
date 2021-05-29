---
title: Zabezpečení
description: Seznamte se s některými koncepty zabezpečení a funkcemi zabezpečení, které vám můžou pomoct efektivně vyvíjet zabezpečené aplikace.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3dcd034a76fbc371c95a2bbf386687830e3b63d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687655"
---
# <a name="secure-applications"></a>Zabezpečené aplikace

Zabezpečení byste měli věnovat pozornost ve všech aspektech vývoje aplikace od návrhu až po nasazení. Začněte tím, že Visual Studio co možná nejvíce bezpečně spustíte. Viz [Uživatelská oprávnění.](../ide/user-permissions-and-visual-studio.md)

Abyste mohli efektivně vyvíjet bezpečné aplikace, měli byste znát základní principy konceptů zabezpečení a funkce zabezpečení platforem, pro které vyvíjíte. Také je třeba porozumět bezpečným technikám kódování.

## <a name="code-for-security"></a>Kód pro zabezpečení

K většině chyb kódování, které mají za následek ohrožení zabezpečení, dochází kvůli nesprávným předpokladům vývojářů při práci se vstupem uživatele nebo proto, že plně nerozumí platformě, pro kterou vyvíjejí.

- [Pokyny pro bezpečné kódování](/dotnet/standard/security/secure-coding-guidelines) popisují různé způsoby, jak lze kód .NET navrhovat pro práci se systémem zabezpečení.
- [Osvědčené postupy zabezpečení pro jazyk C++](/cpp/top/security-best-practices-for-cpp) obsahují informace o nástrojích zabezpečení a postupech pro vývojáře v jazyce C++.

## <a name="build-for-security"></a>Sestavení pro zabezpečení

Důležitým aspektem procesu sestavení je také zabezpečení. Několik dalších kroků může zlepšit zabezpečení nasazené aplikace a zabránit neoprávněným reverzním útokům, falšování jejich falšování nebo jiným útokům:

- [Nástroj Dotfuscator](dotfuscator/index.md) je zdarma a pomáhá chránit sestavení .NET před zpětnou technikou a neoprávněným použitím, jako je například neoprávněné ladění.
- [Podepisování silným názvem](managing-assembly-and-manifest-signing.md) lze použít k jednoznačné identifikaci softwarových komponent a zabránění falšování názvu.

## <a name="see-also"></a>Viz také

- [Zabezpečení v .NET](/dotnet/standard/security/index)
- [Zabezpečení Azure](/azure/security/)
- [Windows 10 Mobile zabezpečení](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova zabezpečení platformy](/previous-versions/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [zabezpečení ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [model Windows Forms zabezpečení](/dotnet/framework/winforms/windows-forms-security)
