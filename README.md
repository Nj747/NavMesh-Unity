# Unity AI - Nav Mesh Agent (Basic) :computer:
## Nav Mesh Agent #1
This is a basic Nav Mesh Tutorial using Unity. [Youtube video tutorial](https://www.youtube.com/watch?v=Vn_JQgOWk-U)
![Alt Text](https://github.com/Nj747/NavMesh-Unity/blob/master/pointClick.gif)

You can download the unity package (version 2018) or just copy and paste the code below.
```cs
using UnityEngine;
using UnityEngine.AI;

public class PlayerController : MonoBehaviour
{
    NavMeshAgent nma;
    [SerializeField] Camera cam;

	void Start ()
    {
        nma = GetComponent<NavMeshAgent>();
    }

    private void Update()
    {
        // Fire1 is the left click on the mouse
        if (Input.GetButtonDown("Fire1"))
        {
            Ray ray = cam.ScreenPointToRay(Input.mousePosition);
            RaycastHit hit;

            if (Physics.Raycast(ray, out hit))
            {
                nma.SetDestination(hit.point);
            }
        }
    }
}

```
## Nav Mesh Agent #2 - Jump, Drop and dynamic obstacles
![Alt Text](https://github.com/Nj747/NavMesh-Unity/blob/master/Jump&Drop.gif)

Download the corresponding unity package to see the full project. There's also a YT video. The script to move the objects is this:
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Obstacles : MonoBehaviour
{
    int direction = 1;

    void Start ()
    {
    	InvokeRepeating("ChangeDirection", 0f, 2f);
    }
	
    void ChangeDirection()
    {
        direction = direction * (-1);
    }

    private void Update()
    {
        transform.Translate(Vector3.right * direction * Time.deltaTime);
    }
}
```

Feel free to copy and paste whatever you need. It is basic, but useful for beginners.
