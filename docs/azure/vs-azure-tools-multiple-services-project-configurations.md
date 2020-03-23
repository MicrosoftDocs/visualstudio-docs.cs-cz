---
title: Konfigurace projektu Azure s více konfiguracemi služeb
description: Zjistěte, jak nakonfigurovat projekt cloudové služby Azure změnou souborů ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg a ServiceConfiguration.Cloud.cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 7b9df8c5609c92a6b6631d1ed9fdda8d65e9b605
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301697"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurace projektu Azure v sadě Visual Studio za účelem použití více konfigurací služby

Projekt cloudové služby Azure v sadě `ServiceDefinition.csdef` `ServiceConfiguration.Local.cscfg`Visual `ServiceConfiguration.Cloud.cscfg`Studio obsahuje tři konfigurační soubory: , a :

- `ServiceDefinition.csdef`se nasadí do Azure k popisu požadavků cloudové služby a jejích rolí a poskytnout nastavení, která platí pro všechny instance. Nastavení lze číst za běhu pomocí rozhraní Azure Service Hosting Runtime API. Tento soubor lze aktualizovat v Azure pouze v případě, že je zastavena cloudová služba.
- `ServiceConfiguration.Local.cscfg`a `ServiceConfiguration.Cloud.cscfg` zadejte hodnoty pro nastavení v definičním souboru a určete počet instancí, které mají být spuštěny pro každou roli. Soubor "Místní" obsahuje hodnoty používané v místním ladění; soubor "Cloud" se nasadí `ServiceConfiguration.cscfg` do Azure jako a poskytuje nastavení pro prostředí serveru. Tento soubor lze aktualizovat, zatímco vaše cloudová služba běží v Azure.

Nastavení konfigurace jsou spravovány a upravovány v sadě Visual Studio pomocí stránek vlastností pro příslušnou roli (klikněte pravým tlačítkem myši na roli a vyberte **vlastnosti**nebo poklepejte na roli). Změny mohou být vymezeny podle toho, která konfigurace je vybrána v rozevíracím souboru **Konfigurace služby.** Vlastnosti webových a pracovních rolí jsou podobné, s výjimkou případů popsaných v následujících částech.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Informace o podkladových schématech pro definici služby a konfigurační soubory služby naleznete v článcích [schématu XML .csdef XML](/azure/cloud-services/schema-csdef-file) a [.cscfg XML Schema.](/azure/cloud-services/schema-cscfg-file) Další informace o konfiguraci služby naleznete v [tématu Konfigurace cloudových služeb](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Konfigurační stránka

### <a name="service-configuration"></a>Konfigurace služby

Vybere soubor, který `ServiceConfiguration.*.cscfg` bude ovlivněn změnami. Ve výchozím nastavení existují místní a cloudové varianty a můžete použít příkaz **Spravovat...** ke kopírování, přejmenování a odebrání konfiguračních souborů. Tyto soubory jsou přidány do projektu cloudové služby a zobrazí se v **Průzkumníku řešení**. Přejmenování nebo odebrání konfigurací však lze provést pouze z tohoto ovládacího prvku.

### <a name="instances"></a>Instance

Nastavte vlastnost **Počet instancí** na počet instancí, které by měla služba spustit pro tuto roli.

Nastavte vlastnost **velikost i virtuálního počítače** na extra **malé,** **malé,** **střední,** **velké**nebo **extra velké**.  Další informace najdete v článku [Velikosti cloudových služeb](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Akce spuštění (pouze webová role)

Nastavte tuto vlastnost, která určuje, že Visual Studio by měl spustit webový prohlížeč pro koncové body HTTP nebo koncové body HTTPS nebo obojí při spuštění ladění.

Možnost **koncového bodu HTTPS** je k dispozici pouze v případě, že jste již definovali koncový bod HTTPS pro vaši roli. Koncový bod HTTPS můžete definovat na stránce vlastností **Koncové body.**

Pokud jste již přidali koncový bod HTTPS, možnost koncového bodu HTTPS je ve výchozím nastavení povolena a Visual Studio spustí prohlížeč pro tento koncový bod při spuštění ladění, kromě prohlížeče pro koncový bod HTTP, za předpokladu, že jsou povoleny obě možnosti spuštění.

### <a name="diagnostics"></a>Diagnostika

Ve výchozím nastavení je pro webovou roli povolena diagnostika. Projekt cloudové služby Azure a účet úložiště jsou nastaveny na použití emulátoru místního úložiště. Až budete připraveni k nasazení do Azure, můžete místo toho vybrat tlačítko tvůrce (**...**) a použít úložiště Azure. Diagnostická data můžete přenést do účtu úložiště na vyžádání nebo v automaticky naplánovaných intervalech. Další informace o diagnostice Azure najdete [v tématu Povolení diagnostiky v Cloudových službách Azure a virtuálních počítačích](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Stránka Nastavení

Na stránce **Nastavení** můžete do konfigurace přidat nastavení jako dvojice název-hodnota. Kód spuštěný v roli můžete číst hodnoty nastavení konfigurace za běhu pomocí tříd poskytovaných [spravované knihovny Azure](/previous-versions/azure/dn602775(v=azure.11)), konkrétně [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) metoda.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurace připojovacího řetězce pro účet úložiště

Připojovací řetězec je nastavení, které poskytuje informace o připojení a ověřování pro emulátor úložiště nebo pro účet úložiště Azure. Kdykoli kód v roli přistupuje k úložišti Azure (objekty BLOB, fronty nebo tabulky), potřebuje připojovací řetězec.

> [!Note]
> Připojovací řetězec pro účet úložiště Azure musí používat definovaný formát (viz [Konfigurace připojovacích řetězců úložiště Azure).](/azure/storage/common/storage-configure-connection-string)

Připojovací řetězec můžete nastavit tak, aby používal místní úložiště podle potřeby, a pak nastavit na účet úložiště Azure při nasazení aplikace cloudové služby. Selhání správně nastavit připojovací řetězec může způsobit, že vaše role není možné spustit nebo cykonoběh přes inicializace, zaneprázdněn a zastavení stavy.

Chcete-li vytvořit připojovací řetězec, vyberte **Přidat nastavení** a nastavte **typ** na "Připojovací řetězec".

U nových nebo existujících připojovacích řetězců vyberte **...** * vpravo od pole **Hodnota** otevřete dialogové okno **Vytvořit připojovací řetězec úložiště:**

1. V části **Připojit pomocí**vyberte možnost **Vaše předplatné** a vyberte účet úložiště z předplatného. Visual Studio pak získá pověření účtu úložiště `.publishsettings` automaticky ze souboru.
1. Výběr **ručně zadaných přihlašovacích údajů** umožňuje zadat název účtu a klíč přímo pomocí informací z portálu Azure. Kopírování klíče účtu:
    1. Přejděte na účet úložiště na webu Azure Portal a vyberte **Spravovat klíče**.
    1. Pokud chcete klíč účtu zkopírovat, přejděte na účet úložiště na webu Azure Portal, vyberte **Nastavení > přístupové klíče**a potom pomocí tlačítka copy zkopírujte primární přístupový klíč do schránky.
1. Vyberte jednu z možností připojení. **Zadejte vlastní koncové body,** které vás požádají o určení konkrétních adres URL pro objekty BLOB, tabulky a fronty. Vlastní koncové body umožňují používat [vlastní domény](/azure/storage/blobs/storage-custom-domain-name) a přesněji řídit přístup. Viz [Konfigurace připojovacích řetězců úložiště Azure](/azure/storage/common/storage-configure-connection-string).
1. Vyberte **OK**, pak **soubor > Uložit** aktualizovat konfiguraci s novým připojovacím řetězcem.

Znovu při publikování aplikace do Azure, zvolte konfiguraci služby, která obsahuje účet úložiště Azure pro připojovací řetězec. Po publikování aplikace ověřte, že aplikace funguje podle očekávání vůči službám úložiště Azure.

Další informace o aktualizaci konfigurací služeb naleznete v části [Správa připojovacích řetězců pro účty úložiště](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Stránka Koncový bod

Webová role má obvykle jeden koncový bod HTTP na portu 80. Role pracovního procesu, na druhé straně může mít libovolný počet koncových bodů HTTP, HTTPS nebo TCP. Koncové body mohou být vstupní koncové body, které jsou k dispozici pro externí klienty nebo interní koncové body, které jsou k dispozici pro jiné role, které jsou spuštěny ve službě.

- Chcete-li zpřístupnit koncový bod HTTP externím klientům a webovým prohlížečům, změňte typ koncového bodu na vstup a zadejte název a číslo veřejného portu.
- Chcete-li zpřístupnit koncový bod HTTPS externím klientům a webovým prohlížečům, změňte typ koncového bodu na **vstup**a zadejte název, číslo veřejného portu a název certifikátu správy. Před zadáním certifikátu pro správu je také nutné definovat certifikát na stránce **vlastností Certifikáty.**
- Chcete-li zpřístupnit koncový bod pro interní přístup jinými rolemi v cloudové službě, změňte typ koncového bodu na interní a zadejte název a možné privátní porty pro tento koncový bod.

## <a name="local-storage-page"></a>Stránka místního úložiště

Stránku vlastností **Místní úložiště** můžete použít k rezervaci jednoho nebo více prostředků místního úložiště pro roli. Prostředek místního úložiště je rezervovaný adresář v systému souborů virtuálního počítače Azure, ve kterém je spuštěna instance role.

## <a name="certificates-page"></a>Stránka certifikátů

Stránka **vlastností Certifikáty** přidává informace o certifikátech do konfigurace služby. Všimněte si, že vaše certifikáty nejsou zabaleny s vaší službou; Certifikáty musíte nahrát samostatně do Azure prostřednictvím [portálu Azure](https://portal.azure.com).

Přidání certifikátu zde přidá informace o certifikátech do konfigurace služby. Certifikáty nejsou součástí služby; certifikáty musíte nahrát samostatně prostřednictvím portálu Azure.

Chcete-li přidružit certifikát k roli, zadejte název certifikátu. Tento název se používá k odkazování na certifikát při konfiguraci koncového bodu HTTPS na stránce **Koncové body.** Dále určete, zda je úložiště certifikátů **místní počítač** nebo **aktuální uživatel** a název úložiště. Nakonec zadejte kryptografický otisk certifikátu. Pokud je certifikát v úložišti Aktuální uživatel\Osobní (Můj), můžete zadat kryptografický otisk certifikátu výběrem certifikátu z vyplněného seznamu. Pokud se nachází na jiném místě, zadejte hodnotu kryptografického otisku ručně.

Přidáte-li certifikát z úložiště certifikátů, všechny zprostředkující certifikáty jsou automaticky přidány do nastavení konfigurace za vás. Kromě toho tyto zprostředkující certifikáty musí být odeslány do Azure správně nakonfigurovat službu pro SSL.

Všechny certifikáty správy, které přidružíte k vaší službě, se vztahují na vaši službu pouze v případě, že je spuštěna v cloudu. Pokud je vaše služba spuštěna v prostředí místního vývoje, používá standardní certifikát, který je spravován výpočetním emulátorem.
