class PatientRecord:
    def __init__(self, name, arrival_time, treatment_time, urgency_level):
        self.name = name
        self.arrival_time = arrival_time
        self.treatment_time = treatment_time
        self.urgency_level = urgency_level

def first_come_first_serve_scheduling(patients):
    return sorted(patients, key=lambda x: x.arrival_time)

def shortest_job_first_scheduling(patients):
    return sorted(patients, key=lambda x: x.treatment_time)

def priority_based_scheduling(patients):
    return sorted(patients, key=lambda x: -x.urgency_level)

def round_robin_scheduling(patients, time_quantum=10):
    queue = []
    current_time = 0
    execution_order = []

    while patients or queue:
        available_patients = [p for p in patients if p.arrival_time <= current_time]
        queue.extend(available_patients)
        for p in available_patients:
            patients.remove(p)

        if queue:
            current_patient = queue.pop(0)
            if current_patient.treatment_time > time_quantum:
                current_time += time_quantum
                current_patient.treatment_time -= time_quantum
                queue.append(current_patient)
            else:
                current_time += current_patient.treatment_time
                execution_order.append(current_patient)
        else:
            current_time += 1

    return execution_order

patients = [
    PatientRecord('P1', 0, 30, 3),
    PatientRecord('P2', 10, 20, 5),
    PatientRecord('P3', 15, 40, 2),
    PatientRecord('P4', 20, 15, 4)
]

fcfs_order = [p.name for p in first_come_first_serve_scheduling(patients)]
sjf_order = [p.name for p in shortest_job_first_scheduling(patients)]
ps_order = [p.name for p in priority_based_scheduling(patients)]
rr_order = [p.name for p in round_robin_scheduling(patients)]

print("First Come First Serve Scheduling:", fcfs_order)
print("Shortest Job First Scheduling:", sjf_order)
print("Priority Based Scheduling:", ps_order)
print("Round Robin Scheduling:", rr_order)

# Determine the best scheduling algorithm and mention the algorithm name
algorithm_orders = {
    "First Come First Serve Scheduling": fcfs_order,
    "Shortest Job First Scheduling": sjf_order,
    "Priority Based Scheduling": ps_order,
    "Round Robin Scheduling": rr_order
}

best_algorithm_name = min(algorithm_orders, key=lambda x: len(algorithm_orders[x]))
best_algorithm_order = algorithm_orders[best_algorithm_name]

print("The best scheduling algorithm for this case is:", best_algorithm_name)
print("Order of patients for the best algorithm:", best_algorithm_order)
