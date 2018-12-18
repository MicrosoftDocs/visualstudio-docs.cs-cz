---
title: Sccget – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78c766e52278c8bae29e57cad6f1c0255de4ea43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761717"
---
# <a name="sccget-function"></a>SccGet – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce načte kopii jeden nebo více souborů pro zobrazení a kompilace, ale ne pro úpravy. Ve většině systémů jsou soubory označené jako jen pro čtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in správy zdrojového kódu.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 %{nfiles/  
 [in] Počet souborů podle `lpFileNames` pole.  
  
 lpFileNames  
 [in] Pole plně kvalifikované názvy souborů, které se mají načíst.  
  
 fOptions  
 [in] Příkaz příznaky (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Možností správy zdrojového kódu plug-konkrétní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Úspěšné operaci get.|  
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|  
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu nepodporuje tuto operaci.|  
|SCC_E_FILEISCHECKEDOUT|Nelze získat soubor, který uživatel aktuálně rezervoval.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NOSPECIFIEDVERSION|Zadali jste neplatnou verzi nebo datum a čas.|  
|SCC_E_NONSPECIFICERROR|Obecná chyba; Soubor nebyl synchronizován.|  
|SCC_I_OPERATIONCANCELED|Operace zrušena před dokončením.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je volána s počet a pole názvů souborů, které se mají načíst. Pokud rozhraní IDE předává příznak `SCC_GET_ALL`, to znamená, že položky v `lpFileNames` nejsou soubory, ale adresářů a že všechny soubory pod správou zdrojových kódů v daném adresáři se mají načíst.  
  
 `SCC_GET_ALL` Příznak je možné kombinovat s `SCC_GET_RECURSIVE` příznak načíst všechny soubory v daném adresáři a všech jeho podadresářích.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` měl by být nikdy předán bez `SCC_GET_ALL`. Všimněte si také, že pokud adresáře C:\A a C:\A\B obě předány rekurzivního získat, C:\A\B a všechny jeho podadresáře skutečně načte dvakrát. Zodpovídá za rozhraní IDE, a ne zdrojový ovládací prvek modulu plug-in – abyste měli jistotu, že duplicitní položky, jako je například tento uchovávají mimo pole.  
  
 Nakonec i v případě, že modul plug-in správy zdrojových kódů zadaný `SCC_CAP_GET_NOUI` příznak při inicializaci, která udává, že nemá žádné uživatelské rozhraní pro příkaz Get, tato funkce může stále volat integrovaným vývojovým prostředím, aby načítala soubory. Příznak jednoduše znamená, že rozhraní IDE nezobrazí položku nabídky Get a že modul plug-in není očekává poskytování uživatelského rozhraní.  
  
## <a name="renaming-and-sccget"></a>Přejmenování a sccget –  
 Situace: uživatel rezervuje soubor, například a.txt a změní ho. Před a.txt mohou být vráceny se změnami, druhý uživatel přejmenuje a.txt b.txt v databázi správy zdrojových kódů, rezervuje b.txt, provede určité změny pro soubor a vrátí soubor. První uživatel chce, aby se změny provedené druhý uživatel tak, aby první uživatel přejmenuje jejich místní verzi souboru a.txt b.txt a nemá get na souboru. Místní mezipaměť, která uchovává informace o číslech verzí však stále domnívá první verzi a.txt uložená místně a správy zdrojového kódu nelze tedy přeložit rozdíly.  
  
 Existují dva způsoby, jak vyřešit tuto situaci, kde bude synchronizován s databázi správy zdrojových kódů místní mezipaměť verze ovládacího prvku zdroje:  
  
1.  Nepovolit přejmenování souboru v databázi správy zdrojových kódů, která je právě rezervována.  
  
2.  To ekvivalent "odstranit staré" následované "Přidat nový". Následující požadovaný algoritmus je jedním ze způsobů jak toho dosáhnout.  
  
    1.  Volání [sccquerychanges –](../extensibility/sccquerychanges-function.md) funkce, která se další informace o přejmenování a.txt k b.txt v databázi správy zdrojových kódů.  
  
    2.  Přejmenujte místní a.txt b.txt.  
  
    3.  Volání `SccGet` funkce pro a.txt a b.txt.  
  
    4.  Protože a.txt neexistuje v databázi správy zdrojových kódů, místní verze mezipaměti se vyprazdňují chybějící a.txt informace o verzi.  
  
    5.  Rezervuje soubor b.txt je sloučen s obsah souboru místní b.txt.  
  
    6.  Aktualizované b.txt souboru můžete teď být vráceny se změnami.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)

