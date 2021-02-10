---
title: Podpora standardu FIPS v aplikaci Visual Studio
titleSuffix: ''
description: Přečtěte si, jak Visual Studio podporuje Federal Information Processing Standard publikace 140-2 schválen režim provozu pro Windows, Azure a .NET.
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d6cb0d2bbcb1ec1d13f5916a7c2b1cd97824fb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945536"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Podpora sady Visual Studio pro režim schváleného FIPS 140-2

Od [verze 16,4](/visualstudio/releases/2019/release-notes-v16.4/)Visual Studio 2019 podporuje publikaci Federal Information Processing Standard (FIPS) 140-2 schválený režim provozu pro Windows, Azure a .NET. A s [verzí 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5)Visual Studio teď podporuje režim SCHVÁLENÉho standardu FIPS 140-2 při vývoji [aplikací C++, které cílí na vzdálený systém Linux](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Chcete-li nakonfigurovat režim FIPS 140-2, který je schválen pro sadu Visual Studio, [nainstalujte .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) a pak povolte nastavení zásady skupiny, **Kryptografie systému: pro šifrování, algoritmus hash a podepisování použijte algoritmy kompatibilní se standardem FIPS**.

Další informace o režimu schváleného pro FIPS 140-2 a o tom, jak ho povolit, najdete v tématu [ověření FIPS 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Nástroje, které používáte pro vývoj aplikací pro platformy jiné než Microsoftu, jako je iOS nebo Android, nemusí používat algoritmy kompatibilní se standardem FIPS. Software jiných výrobců, který je součástí sady Visual Studio nebo rozšíření, která nainstalujete, také nemusí používat algoritmy kompatibilní se standardem FIPS. A vývoj pro řešení [služby SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) nepodporuje režim FIPS 140-2 schválený.

## <a name="next-steps"></a>Další kroky

Další informace o režimu schváleného pro Standard FIPS 140-2 pro sadu Visual Studio a další produkty a služby společnosti Microsoft naleznete v následujících odkazech:

- [Visual Studio: nastavení bezpečného vzdáleného vývoje pro systém Linux kompatibilní se standardem FIPS pomocí C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Kryptografie systému a použití algoritmů kompatibilních se standardem FIPS pro šifrování, algoritmus hash a podepisování](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: dodržování standardu FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Viz také

[Zabezpečené aplikace](securing-applications.md)