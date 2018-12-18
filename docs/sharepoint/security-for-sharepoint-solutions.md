---
title: Zabezpečení pro řešení služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b014c3b4ada42982c41928ca17472e3f585af3ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878762"
---
# <a name="security-for-sharepoint-solutions"></a>Zabezpečení pro řešení služby SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zahrnuje následující funkce, které pomáhají zvýšit zabezpečení aplikací služby SharePoint.

## <a name="safe-control-entries"></a>Položky bezpečného řízení
 Každé položky projektu služby SharePoint vytvoří v [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] má **položky bezpečných ovládacích prvků** vlastnost, která představuje bezpečný ovládací prvky kolekce. Jeho **bezpečné** podvlastností umožňuje určit, které považujete za zabezpečené. Další informace najdete v tématu [poskytují informace o nasazení balíčků a v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) a [zadání bezpečných webové části](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>Atribut AllowPartiallyTrustedCallers
 Ve výchozím nastavení můžete přístup pouze aplikace, které jsou plně důvěryhodný pro security (CAS) systémem přístup kódu modulu runtime sestavení sdílené spravovaného kódu. Označení plně důvěryhodná sestavení pomocí atributu AllowPartiallyTrustedCallers umožňuje částečně důvěryhodné sestavení k němu přistupovat.

 Atribut AllowPartiallyTrustedCallers je přidán do jakékoli řešení služby SharePoint, který není nasazený do systému globální mezipaměti sestavení ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). To zahrnuje řešení v izolovaném prostoru nebo nasazení řešení do adresáře Bin aplikace služby SharePoint. Další informace najdete v tématu [změny zabezpečení verze 1 pro rozhraní Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) a [nasazení webové části SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Zabezpečeno proti vlastnosti skriptu
 *Skriptu* je vložení potenciálně škodlivý kód do ovládacích prvků nebo webové stránky. Přispěvatelé pomáhá chránit weby Sharepointu 2010 proti injektáži skriptu, nelze zobrazit nebo upravit webové části nebo jejich vlastnosti ve výchozím nastavení. Toto chování se řídí tím SafeControl – atribut SafeAgainstScript. V [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], nastavte tento atribut v položce projektu **položky bezpečných ovládacích prvků** podvlastností **bezpečné skriptu proti**. Další informace najdete v tématu [poskytují informace o nasazení balíčků a v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) a [postupy: označení ovládacích prvků jako bezpečných](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Vista a Windows 7 nástroj Řízení uživatelských účtů
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] a [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] začlenit funkce zabezpečení označované jako řízení uživatelských účtů (UAC). Pro vývoj řešení služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] a [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systémů nástroje Řízení uživatelských účtů vyžaduje, abyste používali [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako správce systému. Z **Start** nabídky, otevřete místní nabídku pro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a klikněte na tlačítko **spustit jako správce**.

 Ke konfiguraci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zástupce vždy spusťte jako správce, otevřete místní nabídku a zvolte **vlastnosti**, zvolte **Upřesnit** tlačítko **vlastnosti**dialogové okno a potom vyberte **spustit jako správce** zaškrtávací políčko.

 Další informace najdete v tématu [porozumění a nastavení řízení uživatelských účtů ve Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). a [řízení uživatelských účtů Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Důležité informace o oprávnění služby SharePoint
 Pro vývoj řešení služby SharePoint, musí mít dostatečná oprávnění ke spouštění a ladění řešení služby SharePoint. Před otestováním řešení služby SharePoint, proveďte následující kroky k zajištění, že máte potřebná oprávnění:

1.  Přidáte uživatelský účet s oprávněními správce na systému.

2.  Přidáte uživatelský účet jako správce farmy pro SharePoint server.

    1.  V Centrální správy služby SharePoint 2010, zvolte **spravovat skupinu správců farmy** odkaz.

    2.  Na **správci farmy** zvolte **nový** nabídky

3.  Přidejte svůj uživatelský účet ke skupině WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Zvýšení zabezpečení prostředků
 Další informace o problémy se zabezpečením naleznete v následujících tématech.

### <a name="visual-studio-security"></a>zabezpečení produktu Visual Studio

-   [Zabezpečení a uživatelských oprávnění](http://go.microsoft.com/fwlink/?LinkId=177503)

-   [Zabezpečení v nativním kódu a kódu rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)

-   [Zabezpečení v rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>Zabezpečení služby SharePoint

-   [Správa služby SharePoint Foundation a zabezpečení](http://go.microsoft.com/fwlink/?LinkId=177501)

-   [Centrum zabezpečení prostředků služby SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)

-   [Zabezpečení webové části SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

-   [Vylepšení zabezpečení webové aplikace: Hrozby a opatření](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Obecné zabezpečení

-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)

-   [Vytváření aplikací ASP.NET zabezpečené: Ověřování, autorizaci a zabezpečenou komunikaci](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Viz také:

- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)