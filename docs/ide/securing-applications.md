---
title: Zabezpečení
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87f06746901baaaf14f91032f8968a0d99fc20c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595446"
---
# <a name="secure-applications"></a>Zabezpečené aplikace

Zabezpečení byste měli věnovat pozornost ve všech aspektech vývoje aplikace od návrhu až po nasazení. Začněte spuštěním sady Visual Studio co nejbezpečněji. Viz [Uživatelská oprávnění](../ide/user-permissions-and-visual-studio.md).

Abyste mohli efektivně vyvíjet bezpečné aplikace, měli byste znát základní principy konceptů zabezpečení a funkce zabezpečení platforem, pro které vyvíjíte. Také je třeba porozumět bezpečným technikám kódování.

## <a name="code-for-security"></a>Kód pro zabezpečení

Většina chyb kódování, které vedou k ohrožení zabezpečení dochází, protože vývojáři, aby nesprávné předpoklady při práci s vstupem uživatele, nebo protože nejsou plně pochopit platformu, pro které jsou jejich vývoj.

- [Pokyny pro bezpečné kódování](/dotnet/standard/security/secure-coding-guidelines) popisují různé způsoby, jak lze kód .NET navrhnout pro práci se systémem zabezpečení.
- [Doporučené postupy zabezpečení pro c++](/cpp/top/security-best-practices-for-cpp) obsahuje informace o nástrojích zabezpečení a postupech pro vývojáře jazyka C++.

## <a name="build-for-security"></a>Sestavení pro zabezpečení

Zabezpečení je také důležitým aspektem v procesu sestavení. Několik dalších kroků může zlepšit zabezpečení nasazené aplikace a zabránit neoprávněnému zpětnému inženýrství, falšování a jiným útokům:

- [Dotfuscator](dotfuscator/index.md) je zdarma a pomáhá chránit sestavení .NET před reverzní masovou a neautorizovanou funkcí, jako je například neoprávněné ladění.
- [Podepisování silných názvů](managing-assembly-and-manifest-signing.md) lze použít k jednoznačné identifikaci softwarových součástí a zabránění falšování názvů.

## <a name="see-also"></a>Viz také

- [Zabezpečení v .NET](/dotnet/standard/security/index)
- [Zabezpečení Azure](/azure/security/)
- [Průvodce zabezpečením windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkce zabezpečení platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET základní zabezpečení](/aspnet/core/security/?view=aspnetcore-2.1)
- [Zabezpečení modelu Windows Forms](/dotnet/framework/winforms/windows-forms-security)
