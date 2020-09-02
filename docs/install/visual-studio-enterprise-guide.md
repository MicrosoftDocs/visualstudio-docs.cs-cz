---
title: Příručka pro Visual Studio Enterprise
description: Nastavení a řešení potíží se sadou Visual Studio v podnikovém prostředí.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 02ce09aebae0d6e5225ba1cdfa7484aa887135fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247644"
---
# <a name="visual-studio-enterprise-guide"></a>Příručka pro Visual Studio Enterprise
Pokud chcete ušetřit čas během vaší společnosti, která běží na Visual Studiu, začněte tady. Tato podniková příručka obsahuje tipy, které vám pomohou při instalaci a aktualizaci sady Visual Studio v běžných podnikových scénářích, odblokování, pokud dojde k problémům, a Naučte se, jak ohlásit problém, pokud potřebujete další pomoc. 

## <a name="get-started"></a>Začínáme 
Naučte se, jak nasadit Visual Studio do svého podniku v prostředích v síti a v režimu offline. 

- **Pochopení možností pro podnikové nasazení v síťových prostředích**. [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md) nabízí pro správce systému pokyny na základě scénářů. 

- **[Získejte tipy pro řešení potíží](troubleshooting-installation-issues.md)**. Získejte nápovědu při instalaci nebo aktualizaci sady Visual Studio a Naučte se, jak ohlásit problém, pokud jste zablokovali. Tyto tipy obsahují podrobné pokyny, které by měly vyřešit většinu problémů s instalací online nebo offline. 

- **[Vytvořte offline instalaci sady Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Pokud nejste připojení k Internetu nebo máte omezené připojení k Internetu, najděte možnosti pro instalaci sady Visual Studio. 

- **[Vytvořte balíčky zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md)**. Naučte se vytvářet vlastní balíčky zaváděcího nástroje pomocí vytváření manifestů produktů a balíčků. 

- **[Automatické použití kódů Product Key při nasazení sady Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Kód Product Key můžete použít programově jako součást skriptu, který se používá k automatizaci nasazení sady Visual Studio. Kód Product Key můžete na zařízení nastavit programově, a to buď během instalace sady Visual Studio, nebo po dokončení instalace. 

## <a name="install-visual-studio"></a>Instalace sady Visual Studio 

Naučte se instalovat Visual Studio v běžných podnikových scénářích. 

- **[Použijte parametry příkazového řádku k instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Pro řízení a přizpůsobení instalace sady Visual Studio použijte nejrůznější parametry. Automatizujte proces instalace nebo vytvořte mezipaměť instalačních souborů pro pozdější použití. 

- **Viz [Příklady parametrů příkazového řádku pro instalaci sady Visual Studio](command-line-parameter-examples.md)**. Pro ilustraci, jak použít parametry příkazového řádku k instalaci sady Visual Studio, můžete zobrazit několik příkladů, které lze přizpůsobit, aby odpovídaly vašim potřebám. 

- **[Nainstalujte a použijte Visual Studio a služby Azure za bránou firewall nebo proxy server](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Pokud vaše organizace používá bezpečnostní opatření, jako je brána firewall nebo proxy server, pak jsou k dispozici adresy URL domény, které byste mohli chtít přidat do seznamu povolených portů, porty a protokoly, které můžete chtít otevřít, abyste měli k dispozici nejlepší prostředí při instalaci a používání služeb Visual Studio a Azure. 

- **[Vytvořte síťovou instalaci sady Visual Studio](create-a-network-installation-of-visual-studio.md)**. Do mezipaměti ukládat soubory pro počáteční instalaci společně se všemi aktualizacemi produktu do jediné složky.  

## <a name="update-visual-studio"></a>Aktualizace sady Visual Studio 

Přečtěte si, jak úspěšně aktualizovat Visual Studio a opravit problémy s aktualizací. 

- **[Aktualizujte síťovou instalaci sady Visual Studio](update-a-network-installation-of-visual-studio.md)**. Aktualizujte rozložení instalace sítě sady Visual Studio s nejnovějšími aktualizacemi produktu tak, aby bylo možné je použít jako bod instalace pro nejnovější aktualizaci sady Visual Studio, a také k údržbě instalací, které jsou již nasazeny do klientských pracovních stanic.

- **[Aktualizujte si Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)**. Pochopení hodnoty v části aktualizace na základě směrného plánu a zjištění rozdílu mezi podverzemi a aktualizacemi údržby. 

- **[Aktualizujte si Visual Studio pomocí minimálního offline rozložení](update-minimal-layout.md)**. Pro počítače, které nejsou připojené k Internetu, je vytvoření minimálního rozložení nejjednodušší a nejrychlejší způsob aktualizace offline instancí sady Visual Studio.

- ** [Opravte Visual Studio](repair-visual-studio.md) a opravte problémy s aktualizací**. V některých případech se vaše instalace sady Visual Studio stane poškozená nebo poškozená. Oprava je užitečná pro opravy potíží při instalaci mezi všemi operacemi instalace, včetně aktualizací. 

- **Sledujte [základní hodnoty zabezpečení systému Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines)**. Společnost Microsoft se věnuje poskytování zabezpečených operačních systémů, jako jsou Windows 10 a Windows Server, a zabezpečené aplikace, jako je Microsoft Edge. Kromě bezpečnostní záruky svých produktů vám společnost Microsoft taky umožňuje mít přesnou kontrolu nad vašimi prostředími, a to díky různým možnostem konfigurace. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také 

- [Průvodce produktivitou pro Visual Studio](../ide/productivity-features.md)
