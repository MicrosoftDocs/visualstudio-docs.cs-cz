---
title: Správa dokumentů na serveru pomocí třídy ServerDocument
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e91653734b804693584808478e44443563cdb823
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298275"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Správa dokumentů na serveru pomocí třídy ServerDocument
  Můžete použít `ServerDocument` třídu v a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ke správě několika aspektů přizpůsobení na úrovni dokumentu, i když systém Microsoft Office Word a systém Microsoft Office Excel nejsou nainstalované. Můžete provádět následující úlohy:

- Přístup k datům a jejich změna v mezipaměti dat dokumentu nebo sešitu. Další informace najdete v tématu [práce s daty uloženými v mezipaměti v dokumentu](#CachedData).

- Spravujte sestavení vlastního nastavení, které je přidruženo k dokumentu. Další informace najdete v tématu [Správa přizpůsobení dokumentu](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Pochopení třídy ServerDocument
 `ServerDocument`Třída je navržena pro použití na počítačích, na kterých není sada Office nainstalována. Proto tuto třídu obvykle používáte v aplikacích, které nejsou integrovány se sadou Office, jako jsou projekty konzoly nebo model Windows Forms projekty, nikoli projekty systému Office. Použijte <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu v sestavení *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 `ServerDocument`Třídu lze použít pro práci s přizpůsobeními na úrovni dokumentu, které byly vytvořeny pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Další informace o nástrojích Visual Studio 2010 Tools for Office runtime a rozšířeních Office pro .NET Framework najdete v tématu [Přehled modulu Runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Pokud máte starší verzi aplikace, která používá `ServerDocument` třídu v `Visual Studio Tools for Office` systému (verze 3,0 Runtime), je `Visual Studio Tools for Office` nutné nainstalovat systém (verze 3,0 Runtime) na počítačích, na kterých je aplikace spuštěna. `Visual Studio 2010 Tools for Office runtime`Tyto aplikace nelze spustit.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Práce s daty uloženými v mezipaměti v dokumentu
 `ServerDocument`Třída poskytuje členy, které můžete použít pro práci s datovou mezipamětí v přizpůsobených dokumentech. Další informace o datech uložených v mezipaměti najdete v tématu [ukládání dat do mezipaměti](../vsto/caching-data.md) a [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).

 Následující tabulka uvádí členy, které můžete použít pro práci s daty uloženými v mezipaměti.

|Úloha|Člen, který se má použít|
|----------|-------------------|
|K určení, zda má dokument datovou mezipaměť.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>Metoda.|
|Pro přístup k datům uloženým v mezipaměti v dokumentu.<br /><br /> Další informace najdete v tématu [přístup k datům v dokumentech na serveru](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>Vlastnost.|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Správa přizpůsobení dokumentu
 Členy třídy můžete použít `ServerDocument` ke správě sestavení vlastního nastavení, které je přidruženo k dokumentu. Můžete například programově odebrat vlastní nastavení z dokumentu, aby už dokument nebyl součástí vlastního nastavení.

 Následující tabulka uvádí členy, které můžete použít ke správě sestavení vlastního nastavení.

|Úloha|Člen, který se má použít|
|----------|-------------------|
|K určení, zda je dokument součástí přizpůsobení na úrovni dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>Metoda.|
|K programovému připojení vlastního nastavení k dokumentu v době běhu.<br /><br /> Další informace najdete v tématu [Postup: připojení rozšíření spravovaného kódu k dokumentům.](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Jedna z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metod.|
|Pro programové odebrání přizpůsobení z dokumentu v době běhu.<br /><br /> Další informace najdete v tématu [Postup: odebrání rozšíření spravovaného kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>Metoda.|
|Získat adresu URL manifestu nasazení, který je přidružen k dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>Vlastnost.|

## <a name="see-also"></a>Viz také
- [Postupy: připojení rozšíření spravovaného kódu k dokumentům](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Postupy: odebrání rozšíření spravovaného kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Data mezipaměti](../vsto/caching-data.md)
