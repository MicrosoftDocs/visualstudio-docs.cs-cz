---
title: Zabezpečení pro řešení služby SharePoint | Microsoft Docs
description: Seznamte se s funkcemi, které Visual Studio zahrnuje, aby bylo možné lépe zvýšit zabezpečení aplikací SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 588b2af3672851bf7f452287d8383aa2d319347d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881578"
---
# <a name="security-for-sharepoint-solutions"></a>Zabezpečení pro řešení služby SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zahrnuje následující funkce, které vám pomůžou zlepšit zabezpečení aplikací SharePoint.

## <a name="safe-control-entries"></a>Položky bezpečného řízení
 Každá položka projektu služby SharePoint vytvořená v [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] má vlastnost **bezpečného řízení položky** , která představuje kolekci bezpečných ovládacích prvků. Jeho **bezpečná** podvlastnost umožňuje zadat ovládací prvky, které považujete za bezpečné. Další informace naleznete v tématu [poskytnutí informací o balíčku a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) a [určení bezpečného webové části](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers – atribut
 Ve výchozím nastavení mají přístup ke sdílenému sestavení spravovaného kódu pouze aplikace, které jsou plně důvěryhodné pro systém CAS (Code Access Security). Označení plně důvěryhodného sestavení pomocí atributu AllowPartiallyTrustedCallers umožňuje částečně důvěryhodným sestavením přístup k němu.

 Atribut AllowPartiallyTrustedCallers je přidán do jakéhokoli řešení služby SharePoint, které není nasazeno do globální mezipaměti sestavení ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ) systému. To zahrnuje řešení v izolovaném prostoru nebo řešení nasazená do adresáře bin aplikace služby SharePoint. Další informace najdete v tématu [změny zabezpečení verze 1 pro Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) a [nasazení webové části ve službě SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Bezpečná proti vlastnosti skriptu
 Vložení *skriptu* je vložení potenciálně škodlivého kódu do ovládacích prvků nebo webových stránek. Aby mohli přispěvatelé chránit weby SharePoint 2010 proti injektáže skriptu, nemohou je ve výchozím nastavení zobrazovat ani upravovat webové části nebo jejich vlastnosti. Toto chování je řízeno atributem SafeControl – nazvaným SafeAgainstScript. V [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] , nastavte tento atribut v podvlastnosti **položky bezpečného řízení** položky projektu na **bezpečnou proti skriptu**. Další informace naleznete v tématu [poskytnutí informací o balíčku a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) a [Postupy: označení ovládacích prvků jako bezpečných ovládacích prvků](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Řízení uživatelských účtů systému Vista a Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] a [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] Zahrňte funkci zabezpečení, která se nazývá řízení uživatelských účtů (UAC). Pro vývoj řešení služby SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] v [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systémech a vyžaduje nástroj řízení uživatelských účtů spuštění [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako správce systému. V nabídce **Start** otevřete místní nabídku pro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a pak zvolte možnost **Spustit jako správce**.

 Chcete-li nakonfigurovat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zástupce, aby se vždy spouštěl jako správce, otevřete místní nabídku, zvolte možnost **vlastnosti**, klikněte na tlačítko **Upřesnit** v dialogovém okně **vlastnosti** a pak zaškrtněte políčko **Spustit jako správce** .

 Další informace najdete v tématu [Principy a konfigurace řízení uživatelských účtů v systému Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). a [řízení uživatelských účtů systému Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Požadavky na oprávnění služby SharePoint
 Pro vývoj řešení služby SharePoint je nutné mít dostatečná oprávnění ke spouštění a ladění řešení služby SharePoint. Než budete moct otestovat řešení služby SharePoint, proveďte následující kroky, abyste měli jistotu, že máte potřebná oprávnění:

1. Přidejte svůj uživatelský účet jako správce systému.

2. Přidejte svůj uživatelský účet jako správce farmy pro server SharePoint.

    1. V centrální správě SharePoint 2010 vyberte odkaz **spravovat skupinu správců farmy** .

    2. Na stránce **Správci farmy** klikněte na možnost **Nová** nabídka.

3. Přidejte svůj uživatelský účet do skupiny WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Další prostředky zabezpečení
 Další informace o problémech se zabezpečením najdete v následujících tématech.

### <a name="visual-studio-security"></a>zabezpečení produktu Visual Studio

- [Zabezpečení a uživatelská oprávnění](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Zabezpečení v nativním a .NET Frameworkovém kódu](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Zabezpečení v rozhraní .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Zabezpečení služby SharePoint

- [Správa a zabezpečení služby SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Centrum prostředků zabezpečení služby SharePoint](/sharepoint/dev/)

- [Zabezpečení Webové části ve službě SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Vylepšení zabezpečení webových aplikací: hrozby a protiopatření](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Obecné zabezpečení

- [Životní cyklus vývoje zabezpečení MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Sestavování zabezpečených aplikací ASP.NET: ověřování, autorizace a zabezpečená komunikace](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Viz také

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)