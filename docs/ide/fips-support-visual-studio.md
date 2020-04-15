---
title: Podpora visual studia pro schválený provozní režim FIPS 140-2
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386447"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Podpora visual studia pro schválený provozní režim FIPS 140-2

Počínaje [verzí 16.4](/visualstudio/releases/2019/release-notes-v16.4/)podporuje Visual Studio 2019 schválený provozní režim federal information processing standardu (FIPS) pro Windows, Azure a .NET. A s [verzí 16.5](/visualstudio/releases/2019/release-notes-v16.5/)visual studio nyní podporuje fips 140-2 schválený režim provozu při vývoji [aplikací Jazyka C++, které cílí na vzdálený systém Linux](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Chcete-li nakonfigurovat operační režim schválený fips 140-2 pro sady Visual Studio, [nainstalujte rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) a povolte nastavení zásad skupiny **Systémová kryptografie: Použijte algoritmy kompatibilní s FIPS pro šifrování, algoritmus hash a podepisování**.

Další informace o schváleném provozním režimu FIPS 140-2 a o tom, jak jej povolit, naleznete v [tématu FIPS 140-2 Validation](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Nástroje, které používáte k vývoji aplikací pro platformy jiných společností než Microsoft, jako je iOS nebo Android, nemusí používat algoritmy kompatibilní s FIPS. Software jiných výrobců, který je součástí sady Visual Studio nebo rozšíření, která nainstalujete, také nemusí používat algoritmy kompatibilní s FIPS. A vývoj pro [řešení SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) nepodporuje fips 140-2 schválený režim provozu.

## <a name="next-steps"></a>Další kroky

Další informace o schváleném provozním režimu FIPS 140-2 pro sadu Visual Studio a další produkty a služby společnosti Microsoft naleznete v následujících odkazech:

- [Visual Studio: Nastavení zabezpečeného vzdáleného linuxového vývoje kompatibilního s FIPS s C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Systémová kryptografie a použití algoritmů kompatibilních s FIPS pro šifrování, hašování a podepisování](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: Shoda FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Viz také

[Zabezpečené aplikace](securing-applications.md)