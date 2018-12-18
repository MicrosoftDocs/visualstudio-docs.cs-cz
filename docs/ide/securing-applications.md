---
title: Zabezpečení
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87e9cb7e9400253713caab17da04c44eb11f5ed1
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843907"
---
# <a name="secure-applications"></a>Zabezpečené aplikace

Zabezpečení byste měli věnovat pozornost ve všech aspektech vývoje aplikace od návrhu až po nasazení. Spusťte jako bezpečně spuštěním sady Visual Studio. V tématu [oprávnění uživatele](../ide/user-permissions-and-visual-studio.md).

Abyste mohli efektivně vyvíjet bezpečné aplikace, měli byste znát základní principy konceptů zabezpečení a funkce zabezpečení platforem, pro které vyvíjíte. Také je třeba porozumět bezpečným technikám kódování.

## <a name="code-for-security"></a>Kód pro zabezpečení

Protože vývojáři nesprávný předpoklady při práci s uživatelský vstup, nebo protože nemáte porozumí plně platformu, pro kterou provádíte vývoj dojít k většině kódování chybám, jejichž výsledkem ohrožení zabezpečení.

- [Zabezpečené kódování pokyny](/dotnet/standard/security/secure-coding-guidelines) popisuje různé způsoby kód .NET může být navrženy pro práci s zabezpečení systému.
- [Osvědčené postupy zabezpečení pro jazyk C++](/cpp/top/security-best-practices-for-cpp) obsahuje informace o nástrojích zabezpečení a postupy pro vývojáře C++.

## <a name="build-for-security"></a>Sestavení pro zabezpečení

Zabezpečení je také důležitý faktor v procesu sestavení. Pár dalších kroků můžete zlepšit zabezpečení nasazené aplikace a pomáhá zabránit neoprávněnému zpětnou analýzu, falšování identity nebo jiným útokům:

- [Dotfuscatoru](dotfuscator/index.md) volný a pomáhá chránit před zpětnou a neoprávněnému použití například neoprávněným ladění sestavení .NET.
- [Podpis silného názvu](managing-assembly-and-manifest-signing.md) slouží k jednoznačné identifikaci softwarové součásti a zabránit falšování.

## <a name="see-also"></a>Viz také:

- [Zabezpečení v rozhraní .NET Framework](/dotnet/standard/security/index)
- [Zabezpečení Azure](/azure/security/)
- [Průvodce zabezpečením Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Funkce zabezpečení platformy Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Core zabezpečení](/aspnet/core/security/?view=aspnetcore-2.1)
- [Windows Forms – zabezpečení](/dotnet/framework/winforms/windows-forms-security)