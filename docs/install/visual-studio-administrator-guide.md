---
title: Příručka správce sady Visual Studio
titleSuffix: ''
description: Další informace o tom, jak nasadit aplikaci Visual Studio v podnikovém prostředí.
ms.custom: seodec18
ms.date: 05/29/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 358614cae2001f46588bb447d97a863cf19b8036
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159461"
---
# <a name="visual-studio-2017-administrator-guide"></a>Příručka pro správce aplikace Visual Studio 2017

V podnikovém prostředí je běžné, že správce systému nasadit zařízení pro koncové uživatele ze sdílené síťové složce nebo s použitím softwaru pro správu systému. Jsme navrhli tak instalačního modulu Visual Studio pro podporu nasazení v podniku, že správci systému možnost vytvářet instalace umístění v síti, předem nakonfigurovat výchozí nastavení instalace, nasazení během procesu instalace kódy product key a po úspěšné zavedení spravovat aktualizace produktu. Tato příručka pro správce poskytuje pokyny založené na scénářích pro rozsáhlá nasazení v síťovém prostředí.

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>Nasazení v podnikovém prostředí sady Visual Studio 2017

Visual Studio 2017 můžete nasadit do klientských pracovních stanic tak dlouho, dokud každý cílový počítač splňuje [minimální požadavky na instalaci](/visualstudio/productinfo/vs2017-system-requirements-vs). Jestli nasazujete prostřednictvím softwaru, jako je System Center nebo dávkového souboru, je obvykle vhodné kvůli tomu provádět následující kroky:

1. [Vytvoření sdílené síťové složky, která obsahuje soubory produktu Visual Studio](create-a-network-installation-of-visual-studio.md) do umístění v síti.

2. [Vyberte úlohy a komponenty](workload-and-component-ids.md) chcete nainstalovat.

3. [Vytvořte soubor odpovědi](automated-installation-with-response-file.md) , která obsahuje výchozí možnosti instalace. Nebo alternativně [sestavení instalační skript](use-command-line-parameters-to-install-visual-studio.md) , který používá parametry příkazového řádku k řízení instalace.

4. Volitelně můžete [použít volume license product key](automatically-apply-product-keys-when-deploying-visual-studio.md) jako součást instalace skript tak, aby uživatelé nemuseli aktivovat software samostatně.

5. Aktualizace rozložení sítě, které [řídit, kdy doručování aktualizací produktu pro vaše koncové uživatele](controlling-updates-to-visual-studio-deployments.md).

6. Volitelně můžete nastavit klíče registru [řídit, co se uloží do mezipaměti na klientských pracovních stanicích](set-defaults-for-enterprise-deployments.md).

7. Spusťte skript vygenerované v předchozích krocích na vaše cílové vývojářské pracovní stanice pomocí zvolených technologií nasazení.

8. [Aktualizujte vaše umístění v síti s nejnovějšími aktualizacemi](update-a-network-installation-of-visual-studio.md) do sady Visual Studio spuštěním příkazu, který jste použili v kroku 1 v pravidelných intervalech a přidejte aktualizované součásti.

> [!IMPORTANT]
> Všimněte si, že instalace ze sítě sdílené složky se "nezapomeňte" zdrojové umístění pocházejí. To znamená, že oprava klientského počítače může být nutné se vraťte do sdílené síťové složky, které klient původně nainstalovali. Pečlivě vašemu umístění v síti tak, aby se budou přizpůsobovat dostupnému prostoru životního cyklu, které plánujete mít Visual Studio 2017 klientů se systémy ve vaší organizaci.

## <a name="use-visual-studio-tools"></a>Pomocí nástrojů sady Visual Studio

Máme několik nástrojů, které vám pomůžou [zjišťovat a spravovat nainstalované instance sady Visual Studio](tools-for-managing-visual-studio-instances.md) na klientských počítačích.

> [!TIP]
> Kromě dokumentaci v příručce pro správce, je dobré zdroje informací o instalaci sady Visual Studio 2017 [stavu Chmiela blogu](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="specify-customer-feedback-settings"></a>Určení nastavení zpětné vazby zákazníka

Ve výchozím nastavení instalaci sady Visual Studio umožňuje zpětné vazby od zákazníků. Když povolíte zásady skupiny, můžete nakonfigurovat Visual Studio a zakázání zpětné vazby od zákazníků v jednotlivých počítačích. Uděláte to tak, nastavte zásadu založenou na registru pro následující klíč:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Položka = **OptIn**

Hodnota = (DWORD)
* **0** je zakázána
* **1** výslovného souhlasu

Další informace o nastavení zpětné vazby zákazníka, najdete v článku [programu Visual Studio Customer Experience Improvement](../ide/visual-studio-experience-improvement-program.md) stránky.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio 2017](install-visual-studio.md)
* [Použití parametrů příkazového řádku pro instalaci sady Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
  * [Referenční dokumentace úlohy a ID komponenty](workload-and-component-ids.md)
* [Vytvoření založené na síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Instalace certifikátů vyžadovaných pro offline instalace sady Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatizace sady Visual Studio pomocí souboru odpovědí.](automated-installation-with-response-file.md)
* [Automatické použití kódů Product Key při nasazení sady Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Nastavení výchozích hodnot pro podniková nasazení sady Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md)
* [Aktualizace na základě síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Řízení aktualizací nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
