---
title: 'Postupy: Přidání a odebrání dalších sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4178f1ca5a437c52754199d26a6d39023193aaf8
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219143"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Postupy: Přidání a odebrání dalších sestavení
  Pokud balíček Sharepointu závisí na jiné sestavení, pro funkce nebo data, můžete přidat sestavení do vašeho řešení balíčku (.wsp). Tímto způsobem, SharePoint server zajišťuje, že vlastní sestavení se instalují s balíčkem.  
  
 Můžete také přidat, změnit bezpečné ovládací prvky a souborů prostředků třídy přidružené k sestavení.  
  
## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Přidejte další sestavení, bezpečné ovládací prvky a prostředky třídy  
 Můžete přidat další sestavení do balíčku řešení služby SharePoint. Dodatečná sestavení v řešení v izolovaném prostoru nasazení do globální mezipaměti sestavení, ale položky Sharepointového projektu v řešení v izolovaném prostoru se přidají do databáze obsahu. Bezpečné ovládací prvky a prostředky třídy můžete také přidat na tyto další sestavení. Další informace o bezpečné ovládací prvky najdete v tématu [poskytuje balení a informace o nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) nebo "Vytváření bezpečný ovládací prvek položky" v [nasazení webové části SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### <a name="to-add-an-existing-assembly"></a>Chcete-li přidat existující sestavení  
  
1.  Otevřít **balíček návrháře**. Další informace najdete v tématu [postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Zvolte **Upřesnit** kartu.  
  
3.  Zvolte **přidat** tlačítko a pak zvolte **přidat existující sestavení** ze seznamu.  
  
     **Přidat existující sestavení** zobrazí se dialogové okno.  
  
4.  Zvolte tři tečky (![ASP.NET – Návrhář mobilních řešení Elipsa](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) a klikněte na tlačítko sestavení, které chcete přidat. Doporučujeme používat pro účely přenositelnosti relativní cesta k vybrané sestavení.  
  
5.  Pro **cíl nasazení**, zvolte **GlobalAssemblyCache** přepínač k nasazení sestavení do globální mezipaměti sestavení, nebo zvolte **WebApplication** možnost tlačítko pro nasazení sestavení do složky webovou aplikaci na serveru, na kterém je spuštěna služba SharePoint.  
  
#### <a name="to-add-an-assembly-from-project-output"></a>Chcete-li přidat sestavení z výstupu projektu  
  
1.  Otevřít **balíček návrháře**.  
  
     Další informace najdete v tématu [postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Zvolte **Upřesnit** kartu.  
  
3.  Zvolte **přidat** tlačítko a pak zvolte **přidat sestavení z výstupu projektu** ze seznamu.  
  
     **Přidat sestavení z výstupu projektu** zobrazí se dialogové okno.  
  
4.  V **zdrojový projekt** seznam a vyberte zdrojový projekt, který chcete přidat.  
  
5.  Pro **cíl nasazení**, zvolte **GlobalAssemblyCache** přepínač k nasazení sestavení do globální mezipaměti sestavení, nebo zvolte **WebApplication** možnost tlačítko pro nasazení sestavení do složky webovou aplikaci na serveru, na kterém je spuštěna služba SharePoint.  
  
#### <a name="to-add-a-safe-control"></a>Chcete-li přidat bezpečný ovládací prvek  
  
1.  Otevřít **upravit existující sestavení** dialogové okno. K tomu, otevřete návrhář balíčku, vyberte **Upřesnit** kartu, zvolte sestavení a klikněte na tlačítko **upravit** tlačítko.  
  
2.  V **bezpečné ovládací prvky** podokně, vyberte **kliknutím sem přidáte novou položku** tlačítko.  
  
3.  V **název sestavení** sloupce, zadejte název sestavení.  
  
4.  V **Namespace** sloupce, zadejte název oboru názvů pro bezpečný ovládací prvek.  
  
5.  V **název typu** sloupce, zadejte název typu.  
  
#### <a name="to-add-a-class-resource"></a>Chcete-li přidat prostředek třídy  
  
1.  Otevřít **upravit existující sestavení** dialogové okno. K tomu, otevřete návrhář balíčku, vyberte **Upřesnit** kartu, zvolte sestavení a klikněte na tlačítko **upravit** tlačítko.  
  
2.  V **prostředky třídy** podokně, vyberte **kliknutím sem přidáte novou položku** tlačítko.  
  
3.  V **název_souboru** sloupce, zvolte tři tečky (![elipsa ASP.NET – Návrhář mobilních řešení](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) a zvolte prostředek, který chcete přidat.  
  
## <a name="delete-custom-assemblies"></a>Odstranit vlastní sestavení  
 Můžete odstranit sestavení z balíčku služby SharePoint nebo odstranit bezpečné ovládací prvky a prostředky třídy z existujících sestavení.  
  
#### <a name="to-delete-an-existing-assembly"></a>Chcete-li odstranit existující sestavení  
  
1.  Otevřít **balíček návrháře**. Další informace najdete v tématu [postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Zvolte **Upřesnit** kartu.  
  
3.  V **dodatečná sestavení** podokně zvolte vlastní sestavení, které chcete odstranit.  
  
4.  Zvolte **odstranit** tlačítko.  
  
#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Chcete-li odstranit bezpečný ovládací prvek pro sestavení  
  
1.  Otevřít **upravit existující sestavení** dialogové okno. K tomu, otevřete návrhář balíčku, vyberte **Upřesnit** kartu, zvolte sestavení a klikněte na tlačítko **upravit** tlačítko.  
  
2.  Zvolte bezpečný ovládací prvek, který chcete odstranit.  
  
3.  Stiskněte klávesu Delete.  
  
#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Odstranit prostředek třídy pro sestavení  
  
1.  Otevřít **upravit existující sestavení** dialogové okno. K tomu, otevřete návrhář balíčku, vyberte **Upřesnit** kartu, zvolte sestavení a klikněte na tlačítko **upravit** tlačítko.  
  
2.  Vyberte prostředek, který chcete odstranit.  
  
3.  Stiskněte klávesu Delete.  
  
## <a name="see-also"></a>Viz také:
 [Vytvoření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Postupy: Přidání a odebrání položek z funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
  
