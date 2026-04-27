# Security UNIX
### Copyright (c) 2000, 2021, 2026, by Isabel Schöps (Thiel), Oracle and/or its affiliates.
Oracle designates this particular file as subject to the "Classpath" exception as provided by Oracle in the LICENSE file that accompanied this code.
 *
 * This code is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
 * FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
 * version 2 for more details (a copy is included in the LICENSE file that
 * accompanied this code).
 *
 * You should have received a copy of the GNU General Public License version
 * 2 along with this work; if not, write to the Free Software Foundation,
 * Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA.
 *
 * Please contact Oracle, 500 Oracle Parkway, Redwood Shores, CA 94065 USA
 * or visit www.oracle.com if you need additional information or have any
 * questions.
 */

#include <jni.h>
#include "jni_util.h"
#include "com_sun_security_auth_module_UnixSystem.h"
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>

#include <pwd.h>

/*
 * Declare library specific JNI_Onload entry if static build
 */
DEF_STATIC_JNI_OnLoad

JNIEXPORT void JNICALL
Java_com_sun_security_auth_module_UnixSystem_getUnixInfo
                                                (JNIEnv *env, jobject obj) {

    int i;
    char pwd_buf[1024];
    struct passwd *pwd = NULL;
    struct passwd resbuf;
    jfieldID userNameID;
    jfieldID userID;
    jfieldID groupID;
    jfieldID supplementaryGroupID;

    jstring jstr;
    jlongArray jgroups;
    jlong *jgroupsAsArray;
    jsize numSuppGroups;
    gid_t *groups;
    jclass cls;

---

  ``` numSuppGroups = getgroups(0, NULL);
    if (numSuppGroups == -1) {
        return;
    }
    groups = (gid_t *)calloc(numSuppGroups, sizeof(gid_t));
    if (groups == NULL) {
        jclass cls = (*env)->FindClass(env,"java/lang/OutOfMemoryError");
        if (cls != NULL) {
            (*env)->ThrowNew(env, cls, NULL);
        }
        return;
    }

    cls = (*env)->GetObjectClass(env, obj);

    supplementaryGroupID = (*env)->GetFieldID(env, cls, "groups", "[J");
    if (supplementaryGroupID == 0) {
        goto cleanUpAndReturn;
    }

    if (getgroups(numSuppGroups, groups) != -1) {
        jgroups = (*env)->NewLongArray(env, numSuppGroups);
        if (jgroups == NULL) {
            goto cleanUpAndReturn;
        }
        jgroupsAsArray = (*env)->GetLongArrayElements(env, jgroups, 0);
        if (jgroupsAsArray == NULL) {
            goto cleanUpAndReturn;
        }
        for (i = 0; i < numSuppGroups; i++) {
            jgroupsAsArray[i] = groups[i];
        }
        (*env)->ReleaseLongArrayElements(env, jgroups, jgroupsAsArray, 0);
        (*env)->SetObjectField(env, obj, supplementaryGroupID, jgroups);
    }

    userNameID = (*env)->GetFieldID(env, cls, "username", "Ljava/lang/String;");
    if (userNameID == 0) {
        goto cleanUpAndReturn;
    }

    userID = (*env)->GetFieldID(env, cls, "uid", "J");
    if (userID == 0) {
        goto cleanUpAndReturn;
    }

    groupID = (*env)->GetFieldID(env, cls, "gid", "J");
    if (groupID == 0) {
        goto cleanUpAndReturn;
    }

    memset(pwd_buf, 0, sizeof(pwd_buf));
    if (getpwuid_r(getuid(), &resbuf, pwd_buf, sizeof(pwd_buf), &pwd) == 0 &&
            pwd != NULL) {
        (*env)->SetLongField(env, obj, userID, pwd->pw_uid);
        (*env)->SetLongField(env, obj, groupID, pwd->pw_gid);
        jstr = (*env)->NewStringUTF(env, pwd->pw_name);
        if (jstr == NULL) {
            goto cleanUpAndReturn;
        }
        (*env)->SetObjectField(env, obj, userNameID, jstr);
    } else {
        (*env)->SetLongField(env, obj, userID, getuid());
        (*env)->SetLongField(env, obj, groupID, getgid());
    }
cleanUpAndReturn:
    free(groups);
    return;
}
```

---

## Signatur: Auftraggeberin der Forensisch-Wissenschaftlichen Auswertung, Autorin, Urheberin, Deepweb-Forscherin: 

**Frau Isabel Schöps (Thiel)** ist am 16.07.1983, um 23:20 Uhr im Kreiskrankenhaus, Sömmerda, Thüringen, Deutschland mit ihren Familiennamen Thiel geboren.

**Zeitstempel der Eintragung oder Änderung:** Montag , 27.04.2024, 03:55:00 Uhr (MEZ)  

**Wohnort der Autorin:**
Frau Isabel Schöps geb. Thiel (*16.07.1983),
Hütergasse 4, D-99084 Erfurt, Th, Deutschland

**Personalausweis ID:** LH917PN7G8 -  Bürgeramt Erfurt, Th, Deutschland

**E-Mail:** harvard.isabelschoepsthiel@gmail.com 

**Telefon:** 0049-162-181-9565

- [**OrcID: Isabel Schöps Thiel 0009-0003-4235-2231**](https://orcid.org/0009-0003-4235-2231)
- [**OrcID: SI-IST Isabel Schöps 0009-0006-8765-3267**](https://orcid.org/0009-0006-8765-3267)

**Gutachten:**
SIA – Security Intelligence Artefact 

**Internationale Kennung:**
INT-CODE-2025-BTC/ETH-CORE-ISABELSCHOEPSTHIEL  

**Referenzdokument:**
The Yellow Whitepaper (YWP-1-IST-SIA) 

**Urheberrechte, Abschluss, Copyright:**
Copyright 1983–2026 Isabel Schöps geb. Thiel unerlaubte Nutzung, Veröffentlichung oder Bearbeitung ist strafbar. Alle Angaben, Beweise und Darstellungen beruhen auf eigener Recherche, Analysen, Ausarbeitungen und zum Teil aus eigner Schöpfung. Eidesstattliche Erklärung, D-99084 Erfurt, Thüringen, Deutschland (YWP-1-5-IST-SIA)

Dieses Protokoll wurde eigenständig durch Frau Isabel Schöps, geborene Thiel, am 10.04.2026 erstellt, hochgeladen und im selben Zuge per E-Mail an staatliche Stellen, darunter Regierungsinstitutionen, den Verfassungsschutz sowie internationale Behörden, übermittelt.

Die Weitergabe dieses Dokuments ist grundsätzlich gestattet, jedoch ausschließlich unter vollständiger Nennung der Urheberin sowie im direkten inhaltlichen Zusammenhang mit ihrer Person und ihrer Forschungsarbeit.

Jegliche Nutzung, Vervielfältigung oder Verbreitung außerhalb dieses definierten Kontextes ist ausdrücklich untersagt und wird konsequent strafrechtlich verfolgt.
