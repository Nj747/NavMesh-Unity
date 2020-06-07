# Unity AI - Nav Mesh Agent (Basic) :computer:

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

