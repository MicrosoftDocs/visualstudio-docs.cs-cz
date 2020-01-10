---
title: Řešení potíží s programem Help Viewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2cedc9f45d2e21684496bd882de4aa74b3bf8b3d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851071"
---
# <a name="troubleshooting-the-help-viewer"></a>Řešení potíží s programem Help Viewer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje problémy, se kterými se můžete setkat v aplikaci Help Viewer.

## <a name="audio-doesnt-work"></a>Zvuk nefunguje.
 Aplikace Help Viewer neobsahuje zvukový přehrávač. Pokud stahujete obsah obsahující zvuk a nedojde k tomu, když vyberete možnost **Přehrát**, nainstalujte zvukový přehrávač.

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Hledání nefunguje v systému Windows Server 2008, Windows Server 2008 s aktualizací SP1 nebo Windows Server 2008 R2.
 Funkce hledání a filtrování v prohlížeči nápovědy vyžadují, aby byla nainstalovaná a zapnutá služba Windows Search. Ve výchozím nastavení je tato služba vypnuta v systému Windows Server 2008, Windows Server 2008 s aktualizací Service Pack 1 (SP1) a Windows Server 2008 R2.

#### <a name="to-activate-windows-search-service"></a>Aktivace služby Windows Search

1. Spusťte Správce serveru.

2. V levém navigačním podokně vyberte **role**.

3. V podokně Souhrn rolí klikněte na možnost **Přidat roli**.

4. Zvolte roli Souborové služby a pak klikněte na tlačítko **Další** .

5. Vyberte službu role Windows Search.

## <a name="additional-resources"></a>Další materiály a zdroje informací
 Další informace a poskytnutí zpětné vazby v aplikaci Help Viewer můžete získat pomocí následujících zdrojů:

- Pokud chcete poskytnout zpětnou vazbu, přečtěte si článek [Microsoft Connect](https://connect.microsoft.com/) na webu Microsoftu nebo pošlete e-mail na [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).

- Další informace najdete v tématu [dokumentace pro vývojáře a](https://social.msdn.microsoft.com/Forums/en-US/devdocs/threads) fórum k systému pro nápovědu a [na blogu Guy](https://blogs.msdn.com/b/thehelpguy/) .

## <a name="see-also"></a>Viz také
 [Příručka pro správce Help Viewer 2,1](https://msdn.microsoft.com/library/hh492077(VS.110).aspx)
