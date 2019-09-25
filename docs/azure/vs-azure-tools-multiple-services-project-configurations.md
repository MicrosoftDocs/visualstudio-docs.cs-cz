---
title: Konfigurace projektu Azure s několika konfiguracemi služeb
description: Přečtěte si, jak nakonfigurovat projekt cloudové služby Azure změnou souborů ServiceDefinition. csdef, ServiceConfiguration. Local. cscfg a ServiceConfiguration. Cloud. cscfg.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 5314e92065cb29691aca75d424a331d10284a558
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253436"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurace projektu Azure v sadě Visual Studio za účelem použití více konfigurací služby

Projekt cloudové služby Azure v aplikaci Visual Studio zahrnuje tři konfigurační soubory `ServiceDefinition.csdef`: `ServiceConfiguration.Local.cscfg`, `ServiceConfiguration.Cloud.cscfg`a:

- `ServiceDefinition.csdef`je nasazený do Azure a popisuje požadavky cloudové služby a jejích rolí a poskytuje nastavení, která se vztahují na všechny instance. Nastavení je možné číst za běhu pomocí služby Azure hostující běhové rozhraní API. Tento soubor se dá aktualizovat v Azure jenom v případě, že je cloudová služba zastavená.
- `ServiceConfiguration.Local.cscfg`a `ServiceConfiguration.Cloud.cscfg` zadejte hodnoty pro nastavení v definičním souboru a určete počet instancí, které mají být spuštěny pro každou roli. "Místní" soubor obsahuje hodnoty používané při místním ladění; soubor "Cloud" je nasazen do Azure jako `ServiceConfiguration.cscfg` a poskytuje nastavení pro serverové prostředí. Tento soubor se dá aktualizovat, i když je cloudová služba spuštěná v Azure.

Nastavení konfigurace se v aplikaci Visual Studio spravují a upravují pomocí stránek vlastností příslušné role (klikněte pravým tlačítkem na roli a vyberte **vlastnosti**nebo poklikejte na roli). V rozevíracím seznamu **Konfigurace služby** můžou být změny vymezené podle zvolené konfigurace. Vlastnosti pro webovou roli a role pracovního procesu jsou podobné, s výjimkou případů popsaných v následujících oddílech.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Informace o základních schématech pro konfigurační soubory definice služby a konfiguraci služby najdete v článcích schématu [XML. csdef](/azure/cloud-services/schema-csdef-file) a [. cscfg XML](/azure/cloud-services/schema-cscfg-file) . Další informace o konfiguraci služby naleznete v tématu [How to configure Cloud Services](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Konfigurační stránka

### <a name="service-configuration"></a>Konfigurace služby

Vybere, `ServiceConfiguration.*.cscfg` který soubor má vliv na změny. Ve výchozím nastavení existují místní a cloudové varianty a k kopírování, přejmenování a odebírání konfiguračních souborů můžete použít příkaz **Spravovat...** . Tyto soubory se přidají do vašeho projektu cloudové služby a zobrazí se v **Průzkumník řešení**. Přejmenování nebo odebrání konfigurací se ale dá udělat jenom z tohoto ovládacího prvku.

### <a name="instances"></a>Instance

Nastavte vlastnost počet **instancí** na počet instancí, které má služba spustit pro tuto roli.

Nastavte vlastnost **Velikost virtuálního počítače** tak, aby byla větší než **malá**, **malá**, **střední**, **Velká**nebo **velmi velká**.  Další informace najdete v tématu [velikosti pro Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Spouštěcí akce (jenom webová role)

Nastavte tuto vlastnost, pokud chcete určit, že má Visual Studio spustit webový prohlížeč pro koncové body HTTP nebo koncové body HTTPS, nebo při spuštění ladění.

Možnost **koncový bod HTTPS** je dostupná jenom v případě, že jste už pro vaši roli definovali koncový bod HTTPS. Koncový bod HTTPS můžete definovat na stránce vlastností **koncových bodů** .

Pokud jste už přidali koncový bod HTTPS, je ve výchozím nastavení povolená možnost koncový bod HTTPS a Visual Studio spustí prohlížeč pro tento koncový bod při spuštění ladění, a to za předpokladu, že jsou povolené možnosti spuštění.

### <a name="diagnostics"></a>Diagnostika

Ve výchozím nastavení jsou pro webovou roli povoleny diagnostiky. Projekt cloudové služby Azure a účet úložiště se nastaví tak, aby používal emulátor místního úložiště. Až budete připraveni k nasazení do Azure, můžete vybrat tlačítko Tvůrce ( **...** ) a místo toho použít službu Azure Storage. Diagnostická data můžete přenést na účet úložiště na vyžádání nebo v automaticky naplánovaných intervalech. Další informace o diagnostice Azure najdete v tématu [Povolení diagnostiky v azure Cloud Services a Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Stránka Nastavení

Na stránce **Nastavení** můžete přidat nastavení do konfigurace jako páry název-hodnota. Kód spuštěný v roli může číst hodnoty nastavení konfigurace za běhu pomocí tříd poskytovaných [spravovanou knihovnou Azure](http://go.microsoft.com/fwlink?LinkID=171026), konkrétně metodou [GetConfigurationSettingValue](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.getconfigurationsettingvalue.aspx) .

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurace připojovacího řetězce pro účet úložiště

Připojovací řetězec je nastavení, které poskytuje informace o připojení a ověřování pro emulátor úložiště nebo pro účet úložiště Azure. Vždy, když kód v roli přistupuje k Azure Storage (objekty blob, fronty nebo tabulky), potřebuje připojovací řetězec.

> [!Note]
> Připojovací řetězec pro účet úložiště Azure musí používat definovaný formát (viz [konfigurace Azure Storage připojovací řetězce](/azure/storage/common/storage-configure-connection-string)).

Připojovací řetězec můžete nastavit tak, aby v případě potřeby používal místní úložiště, a když nasadíte aplikaci do cloudové služby, nastaví se na účet služby Azure Storage. Chybné nastavení připojovacího řetězce může způsobit, že se vaše role nespustí, nebo se má cyklicky přepínat stav inicializace, zaneprázdnění a zastavení.

Pokud chcete vytvořit připojovací řetězec, vyberte **Přidat nastavení** a nastavit **typ** na připojovací řetězec.

Pro nové nebo existující připojovací řetězce vyberte **...** * napravo od pole **hodnota** otevřete dialogové okno **vytvořit připojovací řetězec úložiště** :

1. V části **připojit pomocí**zvolte možnost **vaše předplatné** a vyberte účet úložiště z předplatného. Visual Studio pak automaticky získá přihlašovací údaje k účtu úložiště ze `.publishsettings` souboru.
1. Po výběru **ručně zadaných přihlašovacích údajů** můžete zadat název účtu a klíč přímo pomocí informací z Azure Portal. Zkopírování klíče účtu:
    1. V Azure Portal přejděte na účet úložiště a vyberte **spravovat klíče**.
    1. Pokud chcete zkopírovat klíč účtu, přejděte na účet úložiště na Azure Portal, vyberte **nastavení > přístupových klíčů**a pak pomocí tlačítka Kopírovat zkopírujte primární přístupový klíč do schránky.
1. Vyberte jednu z možností připojení. **Zadáním vlastních koncových bodů** se zobrazí výzva, abyste zadali konkrétní adresy URL pro objekty blob, tabulky a fronty. Vlastní koncové body umožňují používat [vlastní domény](/azure/storage/blobs/storage-custom-domain-name) a řídit přístup přesně. Viz [Konfigurace připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string).
1. Vyberte **OK**a pak **soubor > Uložit** , aby se konfigurace aktualizovala pomocí nového připojovacího řetězce.

Po publikování aplikace do Azure pak vyberte konfiguraci služby, která obsahuje účet úložiště Azure pro připojovací řetězec. Po publikování aplikace ověřte, že aplikace funguje podle očekávání pro služby Azure Storage.

Další informace o tom, jak aktualizovat konfigurace služby, najdete v části [Správa připojovacích řetězců pro účty úložiště](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Stránka Koncové body

Webová role má obvykle jeden koncový bod HTTP na portu 80. Role pracovního procesu na druhé straně může mít libovolný počet koncových bodů HTTP, HTTPS nebo TCP. Koncovými body můžou být vstupní koncové body, které jsou k dispozici pro externí klienty, nebo interní koncové body, které jsou k dispozici jiným rolím, které jsou spuštěny ve službě.

- Pokud chcete koncový bod HTTP zpřístupnit externím klientům a webovým prohlížečům, změňte typ koncového bodu na vstup a zadejte název a číslo veřejného portu.
- Aby byl koncový bod HTTPS dostupný pro externí klienty a webové prohlížeče, změňte typ koncového bodu na **vstup**a zadejte název, číslo veřejného portu a název certifikátu pro správu. Než budete moci zadat certifikát pro správu, je nutné také definovat certifikát na stránce vlastností **certifikáty** .
- Pokud chcete, aby byl koncový bod dostupný pro interní přístup k jiným rolím v cloudové službě, změňte typ koncového bodu na interní a zadejte název a možné privátní porty pro tento koncový bod.

## <a name="local-storage-page"></a>Stránka místního úložiště

Pomocí stránky vlastností **místního úložiště** můžete rezervovat jeden nebo více prostředků místního úložiště pro roli. Prostředek místního úložiště je rezervovaný adresář v systému souborů virtuálního počítače Azure, ve kterém je spuštěná instance role.

## <a name="certificates-page"></a>Stránka certifikáty

Stránka vlastností **certifikáty** přidává do vaší konfigurace služby informace o certifikátech. Všimněte si, že vaše certifikáty nejsou součástí vaší služby. své certifikáty musíte nahrát samostatně do Azure prostřednictvím [Azure Portal](http://portal.azure.com).

Přidáním certifikátu sem přidáte informace o certifikátech do vaší konfigurace služby. Certifikáty nejsou zabaleny se službou. certifikáty musíte nahrát samostatně prostřednictvím Azure Portal.

Chcete-li přidružit certifikát k roli, zadejte název certifikátu. Tento název se používá pro odkazování na certifikát při konfiguraci koncového bodu HTTPS na stránce **koncové body** . Dále určete, zda je úložiště certifikátů **místní počítač** nebo **aktuální uživatel** a název úložiště. Nakonec zadejte kryptografický otisk certifikátu. Pokud se certifikát nachází v aktuálním úložišti User\Personal (My), můžete zadat kryptografický otisk certifikátu tak, že ho vyberete ze seznamu s vyplněnými certifikáty. Pokud se nachází v jakémkoli jiném umístění, zadejte hodnotu kryptografického otisku ručně.

Když přidáte certifikát z úložiště certifikátů, všechny zprostředkující certifikáty se automaticky přidají do nastavení konfigurace za vás. Kromě toho musí být tyto zprostředkující certifikáty nahrané do Azure, aby bylo možné správně nakonfigurovat službu pro protokol SSL.

Všechny certifikáty pro správu, které přiřadíte ke službě, se vztahují na vaši službu jenom v případě, že běží v cloudu. Když je vaše služba spuštěná v místním vývojovém prostředí, používá standardní certifikát, který je spravovaný emulátorem služby Compute.
