---
title: Práce s úložištěm Subversion
description: Použití Subversion v Visual Studiu pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: d687215bc91dc01a284c49c141a6e52a16ce9e7a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692142"
---
# <a name="working-with-subversion"></a>Práce s úložištěm Subversion

Subversion je centralizovaný systém správy verzí, který umožňuje rezervovat jednu hlavní kopii centralizovaných dat. Na rozdíl od Git, rezervování úložiště Subversion není klonovat celé úložiště, pouze trvá snímek v tomto okamžiku.

Subversion používá model copy-modify-merge, který uživatelům umožňuje pracovat ve stejném úložišti současně. To znamená, že každý uživatel vytvoří místní nebo pracovní kopii centralizovaných dat, na kterých pracují nezávisle. Změny uživatelů pracovníkopie jsou sloučeny chronologicky.

Představte si například, že uživatel A a uživatel B jak rezervovat kopii ze vzdáleného úložiště a každý upravit soubory. Uživatel A dokončí změny a odevzdá je vzdáleně. Předtím, než uživatel B potvrdí svou práci, musí aktualizovat svou pracovní kopii změnami ze vzdáleného zařízení a sloučí se se změnami uživatele A.

V následujících částech se popisuje, jak lze subversion použít pro správu verzí v Sadě Visual Studio pro Mac.

Následující obrázek znázorňuje možnosti poskytované visual studio pro Mac položkou nabídky Správa verzí:

![Položky nabídky Správa verzí](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Pokladna...

Než začnete používat vzdálené úložiště Subversion, podívejte se na úložiště a vytvořte pracovní kopii tohoto adresáře v místním počítači.

Pokud se chcete dozvědět něco o použití funkce **Pokladna** ve Visual Studiu for Mac, postupujte podle pokynů v části [Nastavení úložiště Subversion.](set-up-subversion-repository.md)

## <a name="update-solution"></a>Aktualizovat řešení

Při použití vzdáleného úložiště je důležité mít na paměti, že ostatní uživatelé mohou upravovat soubory, takže vaše pracovní kopie je zastaralá. V očekávání konfliktů se vždy doporučuje vytáhnout všechny změny z úložiště do vašeho řešení před zahájením práce a před potvrzením. Chcete-li provést změny vytahovat, vyberte položku nabídky Řešení **správy verzí > aktualizace.**

## <a name="review-solution-and-commit"></a>Kontrola řešení a potvrzení

Chcete-li zkontrolovat změny v souborech, použijte karty Změny, Navit, Protokol a Sloučit v každém dokumentu, jak je znázorněno na následujícím obrázku:

![Karty správy verzí](media/version-control-vcTabs.png)

Zkontrolujte všechny změny v projektu procházením **položky nabídky Správa verzí > revize a Potvrzení:**

![Řešení recenze](media/version-control-vcStatus.png)

To umožňuje zobrazit všechny změny v každém souboru projektu s možností vrátit, vytvořit opravu nebo potvrdit.

Pokud chcete potvrdit soubor do vzdáleného úložiště, stiskněte Potvrzení..., zadejte zprávu o potvrzení a potvrďte tlačítkem Potvrzení:

![Potvrzení souboru](media/version-control-svnCommit.png)

Tím se změny odešlou do úložiště, kde vytvoří novou revizi všech vašich úprav.

## <a name="see-also"></a>Viz také

- [Nastavení úložiště Subversion](set-up-subversion-repository.md)
