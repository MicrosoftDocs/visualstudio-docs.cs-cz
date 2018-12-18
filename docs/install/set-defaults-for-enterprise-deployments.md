---
title: Výchozí nastavení v případě podnikového nasazení
description: Další informace o zásadách domény a dalších operací konfigurace pro podniková nasazení sady Visual Studio.
ms.date: 05/05/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a173a378ba2165963b8ea9b44e7391807584886b
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159552"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio-2017"></a>Nastavení výchozích hodnot pro podniková nasazení sady Visual Studio 2017

Můžete nastavit zásady registru, které ovlivňují nasazení sady Visual Studio. Tyto zásady jsou globální pro nový instalační program a ovlivnit:

- Kde jsou nainstalované některé balíčky sdílené s jinými verzemi nebo instance
- Kde jsou balíčky v mezipaměti
- Určuje, zda jsou všechny balíčky v mezipaměti

Můžete nastavit některé z těchto zásad, pomocí [možnosti příkazového řádku](use-command-line-parameters-to-install-visual-studio.md), nastavte hodnoty registru na počítači nebo dokonce distribuovat pomocí zásad skupiny v rámci celé organizace.

## <a name="registry-keys"></a>Klíče registru

Existuje několik umístění, kde můžete nastavit výchozí hodnoty enterprise a povolení jejich řízení pomocí zásad skupiny nebo přímo v registru. Visual Studio vyhledá postupně zobrazíte, pokud jsou nastavené žádné zásady organizace; co nejdříve po zjištění hodnota zásad v následujícím pořadí zbývající klíče jsou ignorovány.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (v 64bitových operačních systémech)

> [!IMPORTANT]
> Pokud nenastavíte `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` klíče a místo toho nastavte jeden z jiných klíčů, měli byste nastavit oba klíče v 64bitových operačních systémech. Tento problém je vyřešen v budoucí aktualizace.

Některé hodnoty registru se nastaví automaticky při prvním, jsou použita, pokud nejsou již nastaven. Tento postup zajišťuje, že následné instalace použít stejné hodnoty. Tyto hodnoty jsou uloženy v klíči registru druhý `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Můžete nastavit následující hodnoty registru:

| **Jméno** | **Typ** | **Default** | **Popis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` Nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Ukládají se adresáře, kde manifesty balíček a volitelně datové části. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachovejte datové části balíčku, i když jsou nainstalovány. Kdykoli můžete změnit hodnotu. Zakázání zásady odebere všechny datové části v mezipaměti balíčku pro instanci opravit nebo změnit. Přečtěte si, jak k [zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md) Další informace. |
| `SharedInstallationPath` | `REG_SZ` Nebo `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Adresář, ve kterém jsou nainstalované některé balíčky sdíleny napříč verzemi instance sady Visual Studio. Můžete kdykoli změnit hodnotu, ale mají vliv jenom budoucí nainstaluje. Všechny produkty již nainstalován na původní umístění nesmí být přesunuta, nebo nemusí fungovat správně. |

> [!IMPORTANT]
> Pokud změníte `CachePath` zabezpečené po jakékoli instaluje, je nutné přesunout existující balíček na nové umístění mezipaměti a ověřte, že zásady registru tak, aby `SYSTEM` a `Administrators` mít plnou kontrolu a `Everyone` má přístup pro čtení.
> Nepodařilo se přesunout stávající mezipaměti nebo jeho zabezpečení může způsobit problémy s budoucí nainstaluje.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

 * [Instalace sady Visual Studio](install-visual-studio.md)
 * [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md)
 * [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
